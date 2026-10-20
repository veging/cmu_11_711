# 学习资料仓库（机器人 + 算法 + 英语）

这个仓库用于系统化沉淀日常学习资料，目标是：
- 分类清晰：按主题快速定位资料
- 长期维护：结构稳定、扩展方便
- 便于检索：通过命名规范与索引统一管理

## 1) 推荐目录结构

```text
.
├── README.md
├── .gitignore
├── 01_programming_languages/         # 编程语言（Python/C++/MATLAB 等）
│   ├── README.md
│   ├── python/
│   ├── cpp/
│   └── matlab/
├── 02_cs_fundamentals/               # 计算机基础
│   ├── README.md
│   ├── data_structures/
│   ├── operating_systems/
│   ├── computer_networks/
│   └── databases/
├── 03_frameworks_tools/              # 框架与工具（ROS/Linux/Git/Docker）
│   ├── README.md
│   ├── ros/
│   ├── linux/
│   ├── git/
│   └── docker/
├── 04_algorithms/                    # 算法专题
│   ├── README.md
│   ├── basics/
│   ├── optimization/
│   ├── path_planning/
│   └── machine_learning/
├── 05_robotics/                      # 机器人核心方向
│   ├── README.md
│   ├── control/
│   ├── perception/
│   ├── localization_navigation/
│   └── robot_math/
├── 06_english/                       # 英语学习
│   ├── README.md
│   ├── vocabulary/
│   ├── reading/
│   ├── writing/
│   └── listening_speaking/
├── 07_reading_notes/                 # 读书 / 论文 / 课程笔记
│   ├── README.md
│   ├── books/
│   ├── papers/
│   └── courses/
├── 08_project_practice/              # 项目实践与复盘
│   ├── README.md
│   ├── mini_projects/
│   ├── course_projects/
│   └── competition_notes/
└── 09_index/                         # 全局索引与导航
    ├── README.md
    ├── topics.md
    ├── tags.md
    └── timeline.md
```

> 结构控制在 2~3 层，避免过深目录带来的维护成本。

## 2) 命名规范建议

建议统一命名格式：

```text
YYYY-MM-DD_主题_关键词_类型.md
```

示例：
- `2026-09-10_ros2_tf_tree_note.md`
- `2026-09-11_a_star_path_planning_summary.md`
- `2026-09-12_ielts_reading_false_not_given_drill.md`

推荐类型后缀：
- `note`：知识点记录
- `summary`：阶段总结
- `practice`：练习记录
- `review`：复盘与错题

## 3) 如何新增一个学习主题

1. 先判断归属到哪个顶层目录（如 `05_robotics`）。
2. 若已有子目录，直接新增文件；若没有，先创建新子目录。
3. 按命名规范创建笔记文件（建议 Markdown）。
4. 在 `09_index` 中更新索引（主题入口 + 标签）。
5. 提交前检查：文件名统一、路径合理、无临时文件。

## 4) 推荐笔记格式

**首选 Markdown（`.md`）**：
- 纯文本、跨平台、Git 友好（diff 清晰）
- 可快速全文检索（本地/IDE/GitHub）
- 易于插入代码块、公式、图片链接

补充建议：
- 需要实验过程时，配合 `Jupyter Notebook`（`.ipynb`）
- 最终定稿资料可导出 PDF 归档

## 5) 标签（Tag）与全局索引方案（资料变多时）

可结合“文件内标签 + 全局索引文件”双轨管理：

- 文件内标签（写在文首）
  - 例如：`tags: [robotics, ros2, tf, note]`
- 全局索引（放在 `09_index/`）
  - `topics.md`：按主题汇总入口
  - `tags.md`：按标签倒排（一个标签对应多条资料）
  - `timeline.md`：按日期追踪学习轨迹

建议固定 3 类标签：
- **领域**：`robotics` / `algorithms` / `english`
- **技术点**：`slam` / `dp` / `graph` / `writing`
- **资料类型**：`note` / `summary` / `practice`
