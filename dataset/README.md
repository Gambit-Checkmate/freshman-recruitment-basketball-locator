# 训练数据：篮球单类检测集

这个目录已经可以直接用于 YOLO 训练，不需要进入 Roboflow 下载，也不需要自行标注。

```text
dataset/
├─ data.yaml
├─ train/
│  ├─ images/     # 600 张训练图片
│  └─ labels/     # 与图片同名的 YOLO 标签
└─ valid/
   ├─ images/     # 100 张验证图片
   └─ labels/     # 与图片同名的 YOLO 标签
```

## 标签说明

本数据集只有一个类别：`0 = basketball`。

每个标签文件与图片同名；一行表示一个篮球框：

```text
0 x_center y_center width height
```

其中坐标均已归一化到 0–1，适用于 YOLO 系列模型。

## 来源与整理方式

本教学子集整理自公开的 **Basketball-1 v1** 数据集：

- 原始数据集地址：<https://universe.roboflow.com/eagle-eye/basketball-1zhpe/dataset/1>
- 原始许可：**CC BY 4.0**
- 原始数据共 2,599 张图像，包含 `basketball`、`rim`、`sports ball` 三个类别。

为让第一周任务更聚焦，本仓库仅保留原始标签中的 `basketball` 标注，并从公开训练/验证划分中抽取了 600 张训练图和 100 张验证图。没有使用验收视频的任何画面作为训练数据。
