# 东海凌涛 · 新生纳新任务：篮球定位器

> 第一周视觉工程任务｜目标：完成一个能在视频中定位并标记篮球的程序。

## 直接开始

本仓库已经包含完成任务所需的训练数据与验收视频；**不需要注册 Roboflow，不需要自行找图，不需要自行标注。**

```text
.
├─ dataset/                         # 已整理好的 YOLO 训练集
│  ├─ data.yaml
│  ├─ train/images + train/labels   # 600 张训练图及标签
│  └─ valid/images + valid/labels   # 100 张验证图及标签
└─ evaluation/
   └─ basketball_dribble_evaluation.mp4  # 统一验收视频
```

完整的数据说明请看 [dataset/README.md](dataset/README.md)，验收视频说明请看 [evaluation/README.md](evaluation/README.md)。

## 你需要完成什么

使用队里提供的带标注训练数据，训练或微调一个篮球检测模型；随后让程序读取统一验收视频，在画面中找出篮球，并在篮球周围画出方框或圆圈。

程序需要输出一段新的结果视频。结果视频中应能看到：

- 视频画面中的篮球被持续标记；
- 标记旁显示 `basketball`、置信度或中心点坐标中的至少一项；
- 视频可以正常播放，且不是只展示单张截图。

本任务只检测一个类别：**篮球（`basketball`）**。

## 队里提供的素材

| 素材 | 用途 | 获取方式 |
|---|---|---|
| 篮球检测训练集 | 训练、验证模型 | 本仓库的 [`dataset/`](dataset/) 目录 |
| 统一验收视频 | 跑出最终结果视频 | 本仓库的 [`evaluation/`](evaluation/) 目录 |
| 数据集详情 | 类别、划分与许可 | [`dataset/README.md`](dataset/README.md) |

训练集已经带有目标框标注，可直接按 YOLO 格式使用；**不要求新生自行寻找图片或标注数据**。请不要用验收视频的画面参与训练或调参。

## 推荐技术路线

你可以使用任何实现方式。对零基础同学，推荐：

1. 使用 Python；
2. 使用 Ultralytics YOLO 的预训练权重做微调；
3. 训练时把数据配置指定为 `dataset/data.yaml`；
4. 用 OpenCV 逐帧读取 `evaluation/basketball_dribble_evaluation.mp4`；
5. 将检测框、标签和置信度画回视频；
6. 保存为 `result.mp4`。

模型不必从零训练。使用预训练模型后再在本任务数据集上微调，是符合本任务目标的做法。

## 提交要求

请在截止时间前提交以下两项：

1. **GitHub 仓库链接**
   - 必须包含完整源代码；
   - 必须包含 `README.md`，写清楚安装、训练和运行方式；
   - 必须包含 `requirements.txt` 或等效依赖说明；
   - 不要提交训练产生的权重、运行目录或额外的大视频文件。

2. **QQ 结果视频**
   - 必须以本仓库 `evaluation/` 中的统一视频为输入；
   - 作业请发送至这位学长的QQ号：3570943969
   - 可直接发送导出的视频，或发送录屏。

## 基础验收标准

- 程序能成功读取验收视频；
- 能在大部分篮球清晰可见的画面中标记篮球；
- 导出的结果视频可正常播放；
- GitHub 仓库有可复现的运行说明。

## 加分方向

- 绘制篮球的运动轨迹；
- 对短时遮挡或运动模糊保持更稳定的检测；
- 显示每帧篮球中心坐标；
- 使用跟踪算法减少检测框跳动；
- 对自己的模型、参数和失败场景做简短说明。

## 数据与素材来源

- 训练数据：公开的 Basketball-1 v1 数据集，经本仓库整理为单类 `basketball` YOLO 数据集，原始许可为 **CC BY 4.0**。详见 [`dataset/README.md`](dataset/README.md)。
- 验收视频：Pexels 免费素材，已放在本仓库 `evaluation/` 目录中。详见 [`evaluation/README.md`](evaluation/README.md)。
