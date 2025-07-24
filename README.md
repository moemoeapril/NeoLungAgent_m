

## 🧬 项目简介 | Project Overview

**本项目旨在开发一套基于人工智能的痰液细胞图像分析系统，用于肺癌的早期筛查和辅助诊断。**

我们构建了一个结构化的痰液细胞数据库（包括原始图像及其标注基准），并基于 YOLOv8 和 CNN 模型完成细胞级图像识别与分类任务。在此基础上，引入多模态学习模型（MLM）进行图像+辅助信息联合分析，判断样本是否为阳性，并进一步使用大型语言模型（LLM）对预测结果生成解释性文本，以提升模型输出的临床可读性与决策参考价值。

---

## 🔧 项目功能 | Features

* 📁 **痰液细胞数据库构建**：支持图像切片（patch）自动生成，包含阳性/阴性标签与标注信息。
* 🧠 **YOLOv8 目标检测模型**：用于痰液细胞图像中癌细胞区域的快速识别。
* 🧬 **CNN 分类模型**：对切片图像进行训练，判断是否为癌前病变或可疑阳性样本。
* 🔀 **多模态分析模型（MLLM）**：融合图像特征与生物标志信息，进行联合预测与分析。
* 📖 **LLM解释性输出模块**：基于大语言模型生成自然语言诊断建议，为医生提供可读性良好的决策支持。

---

## 🧪 项目结构 | Project Structure

```
📂 /data
   ├── /raw             # 原始WSI图像 (.ndpi / .kfb)
   ├── /patches         # 切片图像256×256
   └── /labels          # JSON格式的人工标注信息

📂 /models
   ├── /yolov8          # YOLO模型训练与推理代码
   ├── /cnn             # CNN分类模型结构与训练脚本
   └── /mlm_llm         # 多模态学习与LLM解释性输出模块

📂 /scripts
   ├── patch_extract.py # 使用OpenSlide/pyvips进行WSI切图
   ├── train_yolo.py    # YOLOv8训练
   ├── train_cnn.py     # CNN训练
   ├── inference.py     # 整体推理流程（含MLM+LLM）

README.md               # 项目说明文档
requirements.txt        # Python依赖环境
```

---

## 🚀 快速开始 | Quick Start

```bash
# 1. 安装依赖环境
pip install -r requirements.txt

# 2. 提取WSI图像patch
python scripts/patch_extract.py --input data/raw --output data/patches

# 3. 训练YOLOv8模型
python scripts/train_yolo.py --data data/patches

# 4. CNN分类训练
python scripts/train_cnn.py

# 5. 推理与LLM解释输出
python scripts/inference.py --input data/patches/xxx.png
```

---

## 📊 应用场景 | Application Scenarios

* 医疗机构辅助肺癌筛查
* 病理科室细胞病理初筛自动化
* 科研机构细胞图像AI分析应用
* 医学AI模型多模态训练基座构建

---

## 📌 项目状态 | Project Status

✅ 数据集采集与预处理完成
🔄 YOLOv8与CNN模型构建中
🔄 多模态融合模型（MLLM）优化中
🔄 LLM模块支持ChatGLM3 / Qwen等正在测试

---

## 📄 License

[MIT License](./LICENSE)

---

如果你希望我继续补充模型训练指南、贡献指南（CONTRIBUTING.md）或示例 notebook，我可以一并生成。是否需要？
