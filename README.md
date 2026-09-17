# EasyPhoto-models

EasyPhoto 的独立 AI 模型下载仓库。模型通过 **GitHub Releases 附件**分发，不提交到 Git 历史；使用公开下载链接无需登录 GitHub。

## 下载

[模型下载页面](https://github.com/fineday586/EasyPhoto-models/releases/tag/models-2026.09.17.1)

| 功能 | 模型 | 格式 | 上游许可 |
| --- | --- | --- | --- |
| 清晰度增强 / 超分辨率 | Real_HAT_GAN_SRx4 | Core ML，160px FP32 | Apache-2.0 |
| 智能移除 | LaMa | Core ML，800px FP32 | Apache-2.0 |
| 专用降噪 | NAFNet SIDD width32 | Core ML，256px FP32 | MIT，含 BasicSR 声明 |
| 运动去模糊 | Restormer Motion | Core ML，256px FP32 | MIT |
| 本地语音识别 | Whisper small multilingual + Silero VAD 5.1.2 | GGML | MIT |

每个压缩包独立下载，包含模型、来源清单、许可和修改说明。不包含 EasyPhoto 应用、照片、视频、项目或账号信息；没有 Python、安装脚本或可执行程序。

## 软件接入

- Release 的 `model-catalog.json` 提供稳定版本下载 URL、压缩包字节数与 SHA-256，以及解压后文件的逐文件 SHA-256。
- 下载完先验证文件长度和 SHA-256；拒绝绝对路径、父目录跳转、符号链接及清单外文件，再解压到专用临时目录。逐文件校验通过后再安装。
- Core ML 包以 `.mlpackage` 发布，应在用户 Mac 上编译为 `.mlmodelc` 后加载；不要下载或执行任意远程程序。
- 更新模型应发布新版本，避免覆盖旧版本文件。客户端应固定受信任的清单校验值，不把远程最新清单本身当作独立的真实性证明。
- 本仓库提供下载资源；已安装旧版 EasyPhoto 不会因此自动获得模型管理界面，需要后续应用更新接入。

## 来源与许可

- [HAT](https://github.com/XPixelGroup/HAT)
- [LaMa](https://github.com/advimman/lama)
- [NAFNet](https://github.com/megvii-research/NAFNet)
- [Restormer](https://github.com/swz30/Restormer)
- [Whisper](https://github.com/openai/whisper)、[whisper.cpp](https://github.com/ggml-org/whisper.cpp)、[Silero VAD](https://github.com/snakers4/silero-vad)

Core ML 文件是 EasyPhoto 对上游权重的格式转换，不是重新训练；精度、架构提交和权重哈希见包内 `provenance.json`。架构提交不代表未知的训练时提交。各组件保留各自许可，仓库不以统一许可重新授权第三方模型，也不授予 EasyPhoto 应用的源码许可。

AI 增强可能生成不真实细节，不能保证恢复原始信息。HAT 是重型计算模型，大图处理可能耗时数十分钟；请保留原图并核对文字、刻度和产品细节。
