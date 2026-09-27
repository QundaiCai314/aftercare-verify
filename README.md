# aftercare-verify 1.0.0

售后助手的第六个 Skill：根据平台证据、宿主执行回执和操作台账，分别核对平台状态、动作效果、步骤完成与整笔售后终局。

支持执行后核对、主动查进度、用户手动操作后核对及跨会话恢复前读取。Skill 不点击、不提交、不重试、不修改台账、不自行轮询，也不启动 Spark。

## 下载

- [可加载 Skill 包](aftercare-verify-1.0.0.zip)：解压后使用 `aftercare-verify/`。
- [完整工程交付](aftercare-verify-1.0.0-full.zip)：包含 Skill、合成样例、确定性校验、测试与未生效契约提案。
- [测试报告](测试报告.md)
- [契约修订提案](契约修订提案.md)
- [文件摘要](SHA256SUMS.json)

中央契约保持 1.0.0。结果使用 OutcomeReport；提交受理不等于退款完成，平台报告完成不等于独立核验到账。未知发送结果必须先查证，不能通过换 proposal_id 再提交。

## 验证及限制

原始本地交付的26个合成场景与158项确定性检查通过，Skill Creator格式校验通过。包括实际导入前一个Skill的内存执行测试桩；不等于真实ExecutionReceipt服务接通。

没有独立模型前向测试、真实平台联调、生产恢复链路或真实退款验证。平台语义见证为作者合成数据，格式/规则通过不能证明真实售后完成。候选Assessment未启用，生产引用、提案绑定、持久去重和到账来源记录仍需宿主实现。

## 工程复跑

Python 3.10+及jsonschema。从完整包解压目录运行 `python -B -X utf8 tests/run_tests.py`。

两项外部依赖通过环境变量指定：
- `AFTERCARE_CONTRACT_SCHEMA`：对应摘要的中央contracts.schema.json。
- `AFTERCARE_INTERACT_OUTPUTS`：前一个aftercare-interact完整交付根目录。

缺少外部依赖会明确记录未通过，不把跳过当通过。历史158/158记录来自原始本地环境；发布副本去掉本机绝对路径，并将工程测试路径改为上述配置。仅Skill包运行不依赖这些工程路径。

未自动安装到全局，未修改中央接口或已有Skills。文件为本项目合成开发资料，不含真实订单、账户或售后证据。
