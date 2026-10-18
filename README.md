
# 🍎 Fruit Classification Pipeline with ConvNeXt

An advanced end-to-end deep learning image classification pipeline built on the **ConvNeXt-Tiny** architecture, leveraging fine-grained feature representation learning and evaluated using the **CIFAR-100** dataset structure.

## 🔬 Phương Pháp Triển Khai & Kết Quả Thực Nghiệm (Methodology & Results)

Đề tài được tiến hành nghiên cứu và so sánh thông qua **2 hướng tiếp cận chính** nhằm đánh giá hiệu quả giữa việc tự thiết kế mô hình và việc áp dụng kỹ thuật Transfer Learning:

---

### 1. Chi Tiết Hai Hướng Tiếp Cận

| Tiêu chí | 1️⃣ Custom CNN (From Scratch) | 2️⃣ ConvNeXt (Transfer Learning) |
| :--- | :--- | :--- |
| **Kiến trúc** | Mạng CNN tự thiết kế (tầng đầu Conv 7×7, BatchNorm, MaxPool/Dropout) | Kiến trúc hiện đại **ConvNeXt-Tiny** |
| **Khởi tạo trọng số** | Random Initialization (huấn luyện từ đầu) | Pretrained trên bộ dữ liệu **ImageNet-1K** |
| **Mục đích** | Đánh giá khả năng học đặc trưng hình ảnh trực tiếp từ tập dữ liệu đề tài | Tận dụng biểu diễn đặc trưng cấp cao có sẵn và fine-tuning tối ưu hóa |
| **Độ chính xác (Accuracy)** | **63.33%** | **81.19%** |

---

### 2. Đánh Giá & Nhận Xét Kết Quả

* **Custom CNN (63.33%)**:
  * Mô hình tự học toàn bộ các bộ lọc không gian (spatial filters) từ đầu.
  * Mức độ khái quát hóa (generalization) ở mức khá, tuy nhiên còn gặp khó khăn ở các lớp hoa quả có góc chụp phức tạp hoặc hình thái, màu sắc tương đồng nhau.

* **ConvNeXt Transfer Learning (81.19% - Vượt trội +17.86%)**:
  * Nhờ tận dụng trọng số đã được học từ hàng triệu ảnh ImageNet, ConvNeXt dễ dàng trích xuất các đặc trưng hình học, vân bề mặt và màu sắc phức tạp.
  * Tốc độ hội tụ nhanh hơn rõ rệt và độ chính xác phân loại được cải thiện vượt trội trên toàn bộ các lớp.

---

### 3. Ma Trận Nhầm Lẫn (Confusion Matrix)

Dưới đây là ma trận nhầm lẫn chi tiết của 2 phương pháp trên tập kiểm thử (Test Set):

| 🚀 ConvNeXt Transfer Learning (81.19%) | 🧱 Custom CNN from Scratch (63.33%) |
| :---: | :---: |
| ![ConvNeXt Confusion Matrix](convnext_transfer_learning/confusion_matrix.png) | ![Custom CNN Confusion Matrix](cnn_from_scratch/confusion_matrix.png) |
| *Mô hình phân loại đồng đều và tập trung phần lớn giá trị trên đường chéo chính.* | *Mức độ phân tán cao hơn, xuất hiện một số nhầm lẫn giữa các loại quả tương đồng.* |

  <img src="confusion_matrix.png" width="700" alt="Confusion Matrix">
</p>

 The confusion matrix highlights a well-balanced prediction accuracy across target categories. The vast majority of predictions are densely populated along the main diagonal, indicating a high correct-classification rate and minimal confusion between visually similar classes.

