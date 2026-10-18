# 🍎 Fruit Classification Pipeline with ConvNeXt

An advanced end-to-end deep learning image classification pipeline built on the **ConvNeXt-Tiny** architecture, leveraging fine-grained feature representation learning and evaluated using the **CIFAR-100** dataset structure.

---

## 📌 Project Overview & Methodology
This project implements a complete computer vision workflow for image classification, structured into several key phases:
1. **Data Pipeline & Exploration:** Utilizing image data structured from CIFAR-100 (featuring challenging fine-grained categories and diverse object distributions) with robust preprocessing and augmentation.
2. **Model Architecture (ConvNeXt):** Adopting **ConvNeXt**, a pure convolutional network modernized with design principles inspired by Vision Transformers (ViTs)—such as enlarged kernel sizes ($7\times7$), inverted bottlenecks, and GELU activations—balancing local inductive bias with high representational capacity.
3. **Training Strategy:** Optimized using modern deep learning practices to steadily reduce loss and maximize classification accuracy across epochs.
4. **Feature Analysis & Evaluation:** Going beyond standard metrics by extracting high-dimensional embeddings for **t-SNE clustering analysis**, inspecting **first-layer convolutional weights (`conv1`)**, generating **confusion matrices**, and tracking **training dynamics**.

---

## 📂 Repository Structure
* `fruit_classification_pipeline.ipynb`: Main Jupyter Notebook containing the full end-to-end pipeline (data loading, model setup, training, and evaluation).
* `training_history.png`: Training loss and accuracy curves over epochs.
* `tsne_feature_clusters.png`: t-SNE 2D projection visualizing how effectively the model clusters distinct classes.
* `confusion_matrix.png`: Confusion matrix showcasing classification performance and class-wise predictions.
* `conv1_filters_visualization.png`: Visual inspection of the learned weights in the first convolutional layer.

---

## 📊 Results & Detailed Evaluation

### 1. Training Performance
<p align="center">
  <img src="training_history.png" width="800" alt="Training History Curves">
</p>
Biểu đồ thể hiện quá trình hội tụ mượt mà của mô hình qua các epoch. Giá trị Training/Validation Loss giảm sâu ổn định đồng thời tỷ lệ Accuracy tăng trưởng tốt, chứng minh rằng cấu hình siêu tham số (learning rate, optimizer) và kiến trúc ConvNeXt-Tiny tương thích rất hiệu quả với bài toán mà không gặp hiện tượng quá khớp (overfitting) sớm.

### 2. Feature Representation (t-SNE Clusters)
<p align="center">
  <img src="tsne_feature_clusters.png" width="800" alt="t-SNE Feature Clusters">
</p>
Không gian đặc trưng ẩn (latent space) được chiếu xuống 2 chiều thông qua thuật toán t-SNE cho thấy khả năng gom nhóm (clustering) cực kỳ xuất sắc của ConvNeXt. Các điểm dữ liệu thuộc cùng một lớp (class) tạo thành các cụm tách biệt rõ rệt với khoảng cách biên an toàn lớn, chứng tỏ mạng đã học được các đặc trưng phân biệt (discriminative features) rất mạnh mẽ.

### 3. Classification Performance (Confusion Matrix)
<p align="center">
  <img src="confusion_matrix.png" width="700" alt="Confusion Matrix">
</p>
Ma trận nhầm lẫn minh chứng cho độ chính xác phân loại đồng đều trên các lớp mục tiêu. Hầu hết các mẫu dự đoán tập trung dày đặc ở đường chéo chính, thể hiện tỷ lệ dự đoán đúng cao và ít xảy ra hiện tượng nhầm lẫn giữa các nhãn có hình ảnh tương đồng.

