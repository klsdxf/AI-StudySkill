# StudySkill 工作区

本项目维护独立的交互教学 skill，规范入口是 [.agents/skills/studyskill/SKILL.md](.agents/skills/studyskill/SKILL.md)。

- 学生请求开始、继续学习、制订学习计划、实操验收或教学复盘时，使用 `studyskill`；明确调用方式为 `$studyskill`。普通文件维护和讨论 skill 设计不自动开启教学。
- 本项目不注册或重定义 `/upskill`。原 ai-job-search 的 skill、学习档案、验收、复盘和练习均不在本项目的读写流程内，不复制或同步。
- 只有学生开始实际学习后，才在本工作区的 `learning/` 下创建独立学习记录。制作或检查 skill 不代表开始课程、批准教学计划或通过任何验收。
- 所有学习主题共用一份 skill 规范；每个主题的个人计划和状态放在各自学习目录中，不写回 skill。
