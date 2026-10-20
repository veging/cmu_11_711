# 第03节课学习笔记：Frameworks & Tools（ROS/Linux/Git/Docker）

## 学习目标
- 建立“开发环境—中间件—工程协作—部署运行”的完整链路认知。
- 明确 ROS2、Linux、Git、Docker 在机器人项目中的分工。
- 记录常见问题并在对应知识点附近给出处理思路。

## 1. ROS2 核心原理与架构
### 1.1 通信模型（DDS）
- ROS2 采用 DDS 作为底层通信中间件。
- 典型通信形态：
  - Topic（发布/订阅，异步）
  - Service（请求/响应，同步）
  - Action（可取消、可反馈的长任务）

**架构理解（逻辑层）**
1. Node（节点）负责算法与业务逻辑。  
2. Interface（msg/srv/action）定义通信契约。  
3. DDS 负责发现、传输、QoS（可靠性、历史策略等）。

**常见问题（记录在知识点位置）**
- 问题：为什么同一个 Topic 有时“收不到消息”？  
  - 常见原因：QoS 不匹配（如 reliable vs best effort）。
- 问题：节点都启动了，但 `ros2 node list` 看不到？  
  - 常见原因：环境变量未 source、Domain ID 不一致、网络隔离。

### 1.2 工程组织建议
- 一个功能包只做一类职责（感知/定位/控制分开）。
- 接口定义独立维护，避免算法代码与接口耦合。
- launch 文件统一管理启动关系。

## 2. Linux 工具链在学习中的作用
- Shell + 文件系统：保证可复现操作流程。
- 进程管理：`ps`、`top`、`kill` 用于定位运行异常。
- 网络排查：`ping`、`ip a`、`ss -tulnp`。

**常见问题**
- 问题：脚本能执行但命令找不到？  
  - 可能是 PATH 未生效或当前 shell 与配置文件不匹配。
- 问题：权限问题频繁出现？  
  - 先确认文件权限、执行权限，再考虑用户组配置。

## 3. Git 协作模型（学习仓库也适用）
- 基本流：`pull -> branch -> commit -> push -> PR`。
- 提交建议：一次提交只聚焦一个主题（如“补全 lesson03 笔记”）。
- 文档类仓库同样需要清晰的 commit message，便于后续检索。

**常见问题**
- 问题：为什么会出现冲突？  
  - 同一段内容被多个提交修改，需手动合并语义。
- 问题：历史太乱不好回看？  
  - 通过“主题化提交 + 规范命名”降低回溯成本。

## 4. Docker 在学习环境中的价值
- 核心思想：镜像（环境快照）+ 容器（运行实例）。
- 价值：
  - 统一依赖版本
  - 降低“换机/重装”成本
  - 便于课程实验复现

**常见问题**
- 问题：容器里能跑，主机跑不了？  
  - 说明环境依赖未显式记录，应回填到 Dockerfile 或文档。
- 问题：镜像体积过大？  
  - 拆分层、清理缓存、减少不必要依赖。

---

## 附录：语法/命令速查（放在文档末尾）
### A. ROS2 常用命令
```bash
ros2 node list
ros2 topic list
ros2 topic echo /topic_name
ros2 interface show <pkg/msg/Type>
```

### B. Git 常用命令
```bash
git status
git add .
git commit -m "docs: add lesson03 notes"
git pull --rebase
git push
```

### C. Docker 常用命令
```bash
docker build -t my_image:tag .
docker run --rm -it my_image:tag
```
