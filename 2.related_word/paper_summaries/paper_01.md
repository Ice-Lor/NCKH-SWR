# Paper 01 Summary

## Citation

**Tên bài:** E-Commerce Product Categorization Using Machine Learning and Deep Learning Techniques  
(Tên đầy đủ trong bài: "An Image-based Transfer Learning Framework for Classification of E-Commerce Products")  
**Tác giả:** Vrushali Atul Surve  
**Năm:** 2022  
**Nguồn:** MSc Research Project, National College of Ireland  
**DOI/Link:** https://norma.ncirl.ie/6322/1/vrushaliatulsurve.pdf

## Problem (Vấn đề bài báo giải quyết)

Bài báo giải quyết 3 vấn đề chính:

1. **Phân loại sản phẩm thủ công tốn beaucoup thời gian**
   - Ví dụ: Có 10,000 sản phẩm, nhân viên phải tự nhìn và xếp vào từng nhóm (áo/quần/giày)
   - Làm thủ công thì mất hàng tuần, dễ sai sót

2. **Nhiều sản phẩm mới liên tục thêm vào**
   - Trang web bán hàng có thêm sản phẩm mới mỗi ngày
   - Không thể theo kịp nếu làm thủ công

3. **Không biết mô hình AI nào là TỐT NHẤT**
   - Có nhiều mô hình: CNN, VGG19, InceptionV3, ResNet50, MobileNet
   - Chưa rõ mô hình nào vừa chính xác cao vừa chạy nhanh

## Method (Phương pháp/Làm như thế nào)

Bài báo so sánh **5 mô hình AI** để phân loại ảnh sản phẩm:

### 1. CNN (từ đầu)
- **Là gì:** Mạng nơ-ron tích chập, học từ số 0
- **Cách học:** Học trực tiếp từ ảnh sản phẩm, không dùng kiến thức có sẵn
- **Nhược:** Mất nhiều thời gian học (2.5+ giờ), độ chính xác thấp

### 2. Transfer Learning (học chuyển giao) - 4 mô hình
**Ý tưởng:** Thay vì học từ đầu, dùng mô hình đã học sẵn trên hàng triệu ảnh (ImageNet), chỉ tinh chỉnh cho sản phẩm e-commerce

| Mô hình | Đặc điểm | Khi nào dùng |
|---------|----------|--------------|
| **VGG19** | 19 lớp, chính xác trung bình | Dataset nhỏ |
| **InceptionV3** | 48 lớp, của Google, cân bằng giữa tốc độ và chính xác | Cần chính xác cao |
| **ResNet50** | 50 lớp, có "skip connection" giúp học sâu được | Dataset lớn |
| **MobileNet** | Nhẹ, chạy nhanh, dành cho điện thoại | Cần tốc độ cao |

### Quy trình 5 bước:

1. **Thu thập dữ liệu**
   - Lấy từ Kaggle: Dataset Flipkart e-commerce (20,000 sản phẩm)
   - Crawl ảnh từ URL trong file CSV

2. **Làm sạch dữ liệu**
   - Gộp các nhóm con thành nhóm lớn (ví: "Áo thun nữ" + "Áo sơ mi nữ" → "Quần áo nữ")
   - Xóa nhóm có quá ít sản phẩm
   - Sau khi làm sạch: 15 nhóm, 7,755 ảnh

3. **Tăng cường dữ liệu (Data Augmentation)**
   - Tạo ảnh mới từ ảnh cũ bằng cách: lật ngang, lật dọc, xoay, làm mờ
   - Từ 7,755 ảnh → 16,679 ảnh (đủ để train)

4. **Chia dữ liệu**
   - 70% để train (11,675 ảnh)
   - 30% để test (5,004 ảnh)

5. **Train và so sánh 5 mô hình**
   - đo độ chính xác (accuracy)
   - đo thời gian dự đoán (time per image)
   - chọn mô hình TỐT NHẤT

## Dataset (Dữ liệu dùng)

| Đặc điểm | Chi tiết |
|----------|----------|
| **Nguồn** | Kaggle: Flipkart E-commerce Products Dataset  |
| **Số lượng ban đầu** | ~20,000 sản phẩm, 15 cột dữ liệu |
| **Sau khi làm sạch** | 15 nhóm, 7,755 ảnh |
| **Sau khi augment** | 16,679 ảnh (tạo thêm bằng lật/xoay) |
| **Số nhóm (classes)** | 15 nhóm: Quần áo nam, Quần áo nữ, Giày, Phụ kiện, Hương liệu, Văn phòng phẩm, v.v. |
| **Kích thước ảnh** | 224x224 pixel (chuẩn cho CNN) |
| **Chia train/test** | 70% train, 30% test |

## Evaluation (Đo lường như thế nào)

### Các chỉ số dùng:

| Chỉ số | Giải thích đơn giản | Công thức |
|--------|---------------------|-----------|
| **Accuracy (Độ chính xác)** | Trong 100 ảnh thì bao nhiêu ảnh phân loại đúng? | Đúng / Tổng số |
| **Precision** | Trong số mô hình dự đoán là "Áo thun", bao nhiêu cái đúng? | True Positive / (True Positive + False Positive) |
| **Recall** | Trong tất cả ảnh "Áo thun" thật, mô hình tìm được bao nhiêu? | True Positive / (True Positive + False Negative) |
| **F1-Score** | Trung bình hài hòa giữa Precision và Recall | 2 × (Precision × Recall) / (Precision + Recall) |
| **Thời gian** | Mất bao lâu để phân loại 1 ảnh? | giây/ảnh |

### So sánh:
- CNN (train từ đầu)
- VGG19 (transfer learning)
- InceptionV3 (transfer learning)
- ResNet50 (transfer learning)
- MobileNet (transfer learning)

## Results (Kết quả)

### Bảng so sánh 5 mô hình:

| Mô hình | Độ chính xác | Thời gian trung bình | Thời gian train |
|---------|--------------|---------------------|-----------------|
| **CNN** | 51% | 0.426 giây/ảnh | >2.5 giờ |
| **VGG19** | 55% | 0.146 giây/ảnh | <1 giờ |
| **ResNet50** | 76% | 0.126 giây/ảnh | <1 giờ |
| **InceptionV3** | **85%** | 0.137 giây/ảnh | <1 giờ |
| **MobileNet** | **85%** | **0.101 giây/ảnh** | <1 giờ |

### Kết quả chính:

1. **InceptionV3 và MobileNet đều đạt 85% độ chính xác** (cao nhất) 
2. **MobileNet NHANH NHẤT**: 0.101 giây/ảnh (nhanh hơn InceptionV3) 
3. **CNN chậm và kém chính xác nhất**: 51% accuracy, mất 2.5 giờ train 
4. **VGG19 cũng thấp**: 55% accuracy 

### Chi tiết theo nhóm sản phẩm:

| Mô hình | Nhóm dự đoán tốt nhất | Precision | Recall | F1-Score |
|---------|----------------------|-----------|--------|----------|
| CNN | Hương liệu (Fragrance) | 100% | 92% | 83%  |
| VGG19 | Hương liệu (Fragrance) | 100% | 99% | 99%  |
| InceptionV3 | Quần áo nữ (Women-clothing) | 99% | 97% | 98%  |
| ResNet50 | Văn phòng phẩm (School-supplies) | 99% | 91% | 92%  |
| MobileNet | Quần áo nam (Men's-clothing) | 100% | 98% | 99% |

### ĐIỀU QUAN TRỌNG PHÁT HIỆN:

1. **Transfer learning TỐT hơn train từ đầu**
   - CNN (train từ đầu): 51%
   - MobileNet (transfer): 85%
   - Cải thiện **34%** độ chính xác 

2. **MobileNet là TỐT NHẤT tổng thể**
   - Độ chính xác cao (85%) lại NHANH NHẤT (0.101 giây)
   - Phù hợp cho điện thoại, web cần tốc độ cao 

3. **InceptionV3 cũng rất tốt**
   - Cũng 85% accuracy nhưng chậm hơn MobileNet chút
   - Phù hợp khi cần độ chính xác cao hơn tốc độ 

## Limitations (Hạn chế)

1. **CHỈ dùng ảnh, KHÔNG dùng chữ**
   - Không dùng title, mô tả sản phẩm
   - Nếu ảnh mờ/sai thì không có chữ để hỗ trợ 

2. **Dataset nhỏ so với thực tế**
   - Chỉ 16,679 ảnh, 15 nhóm
   - Trang web thật có hàng triệu sản phẩm, hàng trăm nhóm 

3. **Một số nhóm chính xác thấp**
   - Ví dụ: CNN chỉ 51% overall, có nhóm dự đoán sai nhiều
   - Nhóm "Fragrance" bị dự đoán quá nhiều (false positive)

4. **Chưa test trên nhiều nền tảng**
   - Chỉ test trên dataset Flipkart (Ấn Độ)
   - Chưa test trên Amazon, Shopee, Lazada 

5. **Ch chưa tối ưu hyperparameters**
   - Chưa thử nhiều batch size, epoch khác nhau
   - Có thể cải thiện thêm nếu tinh chỉnh kỹ hơn 

## Relevance to our topic (Liên quan gì đến đề tài nhóm)

Bài báo **liên quan TRỰC TIẾP** đến đề tài nhóm "Automated E-commerce Product Categorization and Tagging System Using Convolutional Neural Networks":

| Khía cạnh | Sự liên quan |
|-----------|--------------|
| **Cùng vấn đề** | Tự động phân loại sản phẩm e-commerce bằng ảnh  |
| **Cùng dùng CNN** | Sử dụng CNN và các biến thể (VGG, ResNet, MobileNet) |
| **Ứng dụng thực tế** | Giúp trang web bán hàng tự động xếp sản phẩm  |
| **Transfer learning** | Có thể áp dụng kỹ thuật này cho nhóm |

### Điểm nhóm có thể học từ bài báo:

1. **Dùng transfer learning thay vì train từ đầu**
   - Nhanh hơn, chính xác hơn
   - MobileNet/InceptionV3 là lựa chọn tốt 

2. **So sánh nhiều mô hình trước khi chọn**
   - Đừng chỉ dùng 1 mô hình, hãy thử nhiều cái rồi chọn TỐT NHẤT
   - Bài báo đã so sánh 5 mô hình 

3. **Data augmentation quan trọng**
   - Tạo thêm ảnh từ ảnh cũ giúp mô hình học tốt hơn
   - Bài báo tăng từ 7,755 → 16,679 ảnh

4. **MobileNet là lựa chọn cân bằng**
   - Vừa chính xác cao (85%) lại nhanh (0.101 giây)
   - Phù hợp deploy thực tế 

## Possible improvement (Nhóm có thể cải tiến gì)

### 1. Kết hợp ảnh + chữ (Multimodal) - ĐỂ CẢI云端 WHOLE HỆ THỐNG
- **Bài báo CHI NHisnya ảnh**, nhóm có thể thêm:
  - Title sản phẩm ("Áo thun nam cotton")
  - Mô tả ("Chất liệu cotton, ngắn tay, màu xanh")
  - Thương hiệu (Nike, Adidas)
- **Dùng BERT** để xử lý chữ, kết hợp với CNN cho ảnh
- Dự kiến cải thiện accuracy thêm 5-10% 

### 2. Thử dataset lớn hơn, nhiều nhóm hơn
- Lấy dataset từ Shopee, Lazada Việt Nam
- Test trên 50-100 nhóm thay vì 15 nhóm
- Gần với thực tế hơn 

### 3. Tối ưu MobileNet cho tiếng Việt
- Fine-tune MobileNet trên dataset tiếng Việt
- Thử MobileNetV2, MobileNetV3 (phiên bản mới hơn)
- Deploy lên điện thoại để test tốc độ thật 

### 4. Data augmentation thông minh hơn
- Bài báo chỉ: lật ngang/dọc, xoay, làm mờ
- Nhóm có thể thử:
  - **Mixup**: Ghép 2 ảnh lại
  - **CutMix**: Cắt 1 phần ảnh này dán vào ảnh khác
  - **AutoAugment**: AI tự tìm cách augment TỐT NHẤT
- Giúp mô hình robust hơn 

### 5. Xử lý nhóm hiếm (class imbalance)
- Bài báo: Nhóm "Fragrance" bị dự đoán quá nhiều
- Giải pháp:
  - **Focal loss**: Trọng tâm vào nhóm khó/h hiếm
  - **Oversampling**: Lấy nhiều mẫu hơn từ nhóm hiếm
  - **Undersampling**: Lấy ít mẫu từ nhóm nhiều
- Giúp tất cả nhóm đều chính xác, không chỉ nhóm nhiều 

### 6. Phân loại theo cấp bậc (Hierarchical)
- Bài báo: Phân loại thẳng 1 lớp (15 nhóm)
- Nhóm có thể:
  - Cấp 1: Quần áo → Cấp 2: Áo → Cấp 3: Áo thun
  - Giúp chính xác hơn, dễ giải thích hơn
- Like bài báo trước (IEEE) đã làm 

### 7. Tagging mở rộng (không chỉ category)
- Bài báo: Chỉ phân loại category
- Nhóm có thể thêm:
  - **Màu sắc**: đỏ, xanh, đen
  - **Chất liệu**: cotton, polyester, da
  - **Kiểu dáng**: cổ tròn, cổ V, tay dài
  - **Mục đích**: thể thao, đời thường, đi làm
- Dùng multi-label classification 

### 8. Deploy thật và A/B testing
- Deploy mô hình lên website thật
- A/B test:
  - Nhóm A: Phân loại thủ công (con người)
  - Nhóm B: Phân loại bằng AI
- Đo:
  - Thời gian phân loại 1 sản phẩm
  - Độ chính xác (con người check lại)
  - Ảnh hưởng đến tỷ lệ mua hàng

### 9. Giải thích tại sao (Explainability)
- Bài báo: Không giải thích tại sao mô hình chọn "Áo thun"
- Nhóm có thể:
  - **Grad-CAM**: Hiện vùng ảnh quan trọng
  - **LIME/SHAP**: Giải thích lý do
  - Giúp nhân viên tin tưởng mô hình hơn

### 10. Tiếp tục nghiên cứu multimodal fusion (như bài báo gợi ý)
- Bài báo kết luận: "Future work sẽ nghiên cứu fusion với text"
- Nhóm có thể làm điều này:
  - InceptionV3 cho ảnh
  - BERT/LSTM cho chữ
  - Early Fusion vs Late Fusion
  - Hy vọng accuracy lên 90%+