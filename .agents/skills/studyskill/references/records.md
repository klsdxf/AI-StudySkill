# 独立学习记录约定

开始实际教学或恢复学习时读取。只在本 studyskill 工作区保存新记录，不搜索或借用其他项目的课程。此文件定义记录格式，不包含真实学生数据。

## 路径与职责

项目内使用本项目根目录作为工作区。若 skill 被另行复制使用，则使用该次明确选定的学习工作区；不以当前任意终端目录猜测，也不写进安装后的 skill 文件夹。未明确位置时在首次保存前确认。路径始终约束在选定工作区内。

```text
learning/<topic-id>/
  state.json                    当前进度、确认、规则和断点的唯一状态来源
  events.jsonl                  按时间追加的学习事件
  plans/overall-v1.md            有版本的整体路线
  plans/round-01-v1.md           有版本的整轮计划
  reviews/round-01.md            双向复盘，后续更正追加
  practice/                     学生作品或明确标注的教师示范
  reports/                      需要时生成的派生报告
```

仅在需要时创建相应目录和文件，不生成空报告或虚构练习。`topic-id` 用简短小写字母、数字、连字符命名；已有同名目录先核对课程身份，不覆盖。多个课程分别保存；未明确要继续哪一个时先问。

## 当前状态

`state.json` 使用 JSON，建议字段如下。只有 `schema_version`、`course_id`、`updated_at`、`goal`、`phase`、`current_round`、`plans`、`rounds`、`active_preferences`、`resume`、`last_event_id` 为必需；其他按实际需要添加。

| 字段 | 含义 |
|---|---|
| schema_version | 初始为 1，格式版本 |
| course_id | 与课程目录一致 |
| updated_at | 含时区的实际更新时间 |
| goal | 学生目标、范围、结束条件、原始请求事件；未知保留 null |
| learner | 已知基础、时间与偏好；区分自述和观察，不复制身份或求职档案 |
| phase | intake / overall_planning / round_planning / teaching / review / paused / completed |
| current_round | 当前轮次编号；尚未确定为 null |
| plans | 整体计划版本和相对路径、draft/proposed/approved/superseded、确认事件 |
| rounds | 各轮编号、计划版本及确认事件、标准、学生反馈状态、复盘路径 |
| active_preferences | 当前生效偏好及适用范围、来源事件、被替代关系 |
| resume | 当前问题、学生待做任务或待回答问题、卡点、下一步、暂停前阶段 |
| last_event_id | 已应用到状态的最后事件编号 |

每轮标准至少包含 `id`、`description`、`required`、`status`、`evidence`。标准状态为 `pending`、`passed` 或 `recheck`。`evidence` 是记录列表：来源事件、作品相对路径或对话摘要、观察方式、帮助程度、结果和覆盖限度。尚无证据时用空列表，不能提前填写“通过”。

观察方式区分 `student_report`（本人报告）、`artifact_inspection`（静态检查）、`observed_execution`（实际观察运行）、`observed_response`（学生当场回答）；帮助程度区分 `independent`、`prompted`、`followed_demo`、`assistant_done`。按实际情况组合，助手代做不能满足学生实作标准。

不另存容易失同步的通过总数或整轮通过标志；由必需标准计算。一轮必需项全部 passed 才通过，但进入下轮仍要完成复盘、反馈处理和下轮计划确认。完成全课程还需核对学生目标的结束条件，不能仅因走完所有轮次就自动宣布目标达到。

学生反馈状态使用 `not_requested`、`awaiting_feedback`、`received`、`skipped_by_student`；收到体验不代表同意改线。计划确认必须关联实际学生表态及对应版本，不用日期或助手总结替代。

## 每个有意义的步骤

`events.jsonl` 每行一个 JSON 对象，按时间追加，不重写过去事件。每个教学交互回合记录本回合中的相关事件，而不是等轮末补记。记录足以恢复判断的事实，不逐字复制整段聊天，也不保存隐私、密钥或内部推理。

每条事件包含：

- `id`：课程内单调编号，如 E0001；`at`：带时区的真实时间；`round`：轮次或 null。
- `type`：如 goal、plan_proposed、plan_approved、task、attempt、guidance、evidence、assessment、feedback、adjustment、review、pause、resume、correction。
- `summary`：发生了什么；`source`：学生表态、教师观察或文件。
- `details`：按类型记录具体问题、学生尝试、给过的帮助、观察结果、判断依据、反馈或下一步。
- `related`：相关标准编号、计划版本、先前事件或作品路径。

事件可合并本回合同一任务的紧密动作，但不能只写“继续学习”“完成验收”而丢掉过程。特别记录教师示范程度、学生实际操作、学生体验、调整原因和未验证事项。

验收更正或学生修订用新事件引用旧事件，不删除旧结论。保存用户作品时遵守其协作方式，不用助手版本覆盖学生原作。模拟、演示和学生作品分别标注。

## 保存与恢复

先核对文件的当前内容，基于本回合事实追加事件，再更新 state.json 和相关计划／复盘。更新状态可先写同目录临时文件并核对 JSON 后替换；不要覆盖他人刚产生的更改。

若写入中断，恢复时读取 last_event_id 之后的事件，核对哪些尚未反映到状态，再应用一次。文件冲突时保留现状并澄清，不猜测覆盖。写入失败应明确哪些内容仍未保存。

恢复时以 state.json 定位，再读生效计划、相关完整复盘及必要事件和作品；不能仅靠一份旧报告推断当前位置。复盘追加的新偏好若未同步到状态，按原始学生表态核对并修正。

每轮记录实际时间只有可观察或学生报告才填写；未提供为 null，不从聊天长度推算。报告是展示用途，由状态、计划和事件生成，不反向改写通过结论。普通答疑无需每次新建报告。
