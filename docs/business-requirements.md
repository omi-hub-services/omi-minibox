# Minibox — Tài liệu nghiệp vụ

Phiên bản: 1.0 — Ngày lập: 14/11/2026 — Ngôn ngữ: tiếng Việt.

Trạng thái: đặc tả để triển khai, chưa phải bằng chứng sản phẩm đã được xây dựng hoặc nghiệm thu. Các quyết định phạm vi dưới đây tổng hợp từ 91 câu khám phá; giá trị vận hành trong bảng `CFG` là đề xuất chờ Product Owner (PO) duyệt. Không tự áp dụng các giá trị đó vào production.

## 1. Tầm nhìn và mô hình kinh doanh

Minibox là thương hiệu thương mại điện tử về hệ sinh thái in 3D, tên gọi gợi những chiếc hộp nhỏ. Minibox là bên bán duy nhất, không phải sàn nhiều nhà bán. Ban đầu hoạt động tại Việt Nam dưới hình thức hộ kinh doanh, có thể chuyển thành công ty khi phát triển. Hệ thống lưu phiên bản thông tin pháp lý theo thời gian, không sửa thông tin người bán trên chứng từ lịch sử.

Danh mục gồm đồ trang trí, mô hình trưng bày, figure/anime, bình hoa, chậu cây, đèn ngủ, sản phẩm phục vụ thủy sinh, cùng những ngách có thể mở rộng. Có vật tư/dụng cụ như nhựa in, keo, kìm, kéo và linh kiện. Việc cho phép một nhóm sản phẩm trong phần mềm không chứng minh quyền kinh doanh hoặc độ an toàn của từng mẫu.

Ba nhóm hàng chính:

| Nhóm | Cách cung cấp | Điểm riêng |
|---|---|---|
| Hàng vật lý có sẵn | Xuất từ kho | Có COD, giữ tồn có hạn, giao nhiều đợt |
| Hàng in theo mẫu trong danh mục | Sản xuất sau khi duyệt và nhận đủ cọc | FDM/resin, BOM, máy, vật tư, hậu xử lý, QC |
| File số | Tải sau khi đủ điều kiện | Miễn phí/có phí, bán riêng/bán kèm, giấy phép và cập nhật |

Quy mô dự kiến 6–12 tháng đầu: 1–2 farm, 1–3 kho, tối đa 20 máy, dưới 100 đơn/ngày. Đây là giả định năng lực, không phải giới hạn phần mềm hay dự báo đã kiểm chứng.

Kênh giai đoạn đầu: shop website và đơn do nhân viên tạo trong admin cho điện thoại, Facebook, Zalo, khách mua trực tiếp. Giai đoạn sau: tích hợp Shopee, TikTok Shop, Lazada; quốc tế; nhận file/ý tưởng đặt làm riêng. Không xây marketplace, POS đầy đủ hoặc kế toán tổng hợp trong phạm vi đầu.

## 2. Quy ước phạm vi và quản trị thay đổi

- `COMMITTED`: người dùng đã chốt yêu cầu/phương án trong khám phá.
- `PROPOSED`: mặc định hoặc chi tiết bổ sung do người viết đề xuất; cần duyệt trước khi áp dụng kinh doanh.
- `EXTERNAL`: phụ thuộc hợp đồng, pháp lý, tài khoản hoặc kiểm chứng nhà cung cấp.
- `LATER`: chức năng giai đoạn sau, không tự đưa vào mốc mở bán.
- `M0`–`M6`: các mốc triển khai đề xuất, không có nghĩa chức năng đã hoàn thành.

Toàn bộ yêu cầu giai đoạn đầu phải được giữ trong backlog, dù mở bán trước khi hoàn thành tất cả. Không chuyển một tính năng đã chốt thành “ngoài phạm vi” chỉ để đóng mốc. Muốn thay đổi phạm vi phải có quyết định của PO và cập nhật tiêu chí nghiệm thu.

## 3. Đối tượng và quyền hạn

| Vai trò | Công việc chính | Giới hạn |
|---|---|---|
| Khách vãng lai | Xem, tìm, đặt hàng, đăng ký báo có hàng | Xác minh email để xem dữ liệu riêng/nhận file; chưa dùng xu |
| Khách có tài khoản | Đơn hàng, giấy phép, tải file, Minixu, yêu thích, đánh giá, hỗ trợ | Chỉ dữ liệu của mình |
| Chủ shop/quản trị | Cấu hình, phân quyền, duyệt, báo cáo | Có audit; hành động nhạy cảm phải xác thực lại |
| Bán hàng/CSKH | Tạo/xác nhận đơn, giải quyết yêu cầu | Không tự xác nhận tiền vào nếu không được cấp quyền |
| Điều phối/sản xuất | Duyệt năng lực, farm/máy, mẻ in, tiến độ | Phạm vi farm được giao |
| Nhân viên kho | Nhập/xuất, giữ hàng, điều chuyển, kiểm kê, đóng gói | Phạm vi kho được giao |
| QC/bảo hành | Checklist, phân loại lỗi, xử lý bảo hành | Không tự biến hàng lỗi thành tồn bán được |
| Mua hàng | Nhà cung cấp, đơn mua, nhận hàng, trả nhà cung cấp | Duyệt theo hạn mức |
| Tài chính | Thu/chi, cọc, hoàn tiền, công nợ, COD, hóa đơn | Không sửa/xóa giao dịch đã ghi nhận; dùng điều chỉnh |
| Nội dung | Sản phẩm, blog, media, bình luận | Xuất bản theo quyền và quy trình duyệt |
| Kỹ thuật | Tích hợp, đồng bộ, lỗi, tác vụ nền | Không mặc định có quyền thu/chi hoặc đọc toàn bộ PII |

Một người kiêm nhiều vai trò và nhiều farm/kho. Quyền gồm hành động + phạm vi địa điểm + phạm vi dữ liệu. Không chỉ ẩn menu; truy cập trực tiếp cũng bị kiểm tra. Mọi thay đổi quyền, xuất dữ liệu nhạy cảm, hoàn tiền, điều chỉnh kho và cấu hình tài chính có nhật ký.

Phê duyệt theo loại nghiệp vụ và ngưỡng cấu hình. Có thể cho chủ shop kiêm người tạo/người duyệt trong giai đoạn nhỏ; bật phân tách nhiệm vụ khi cần. Không tự cho người tạo vượt quy tắc bằng cách chia nhỏ giao dịch; tổng các hành động liên quan phải được xét khi quy tắc yêu cầu.

## 4. Danh mục, sản phẩm và giá

### 4.1 Cấu trúc danh mục

`BR-CAT-01`: danh mục nhiều cấp; bộ sưu tập và thẻ độc lập với cây danh mục. Sản phẩm có thể xuất hiện trong nhiều bộ sưu tập. Bộ thuộc tính theo nhóm: đèn có nguồn điện, chậu có thoát nước, thủy sinh có môi trường sử dụng.

`BR-CAT-02`: tách thuộc tính mô tả khỏi thuộc tính tạo biến thể. Mỗi tổ hợp bán được có SKU duy nhất, giá, khối lượng/kích thước, ảnh, phương thức cung cấp, định mức và tồn riêng. Không tạo tất cả tổ hợp không tồn tại; tổ hợp bị vô hiệu hóa không được đặt mới.

`BR-CAT-03`: hỗ trợ `stock_only`, `made_to_order`, `stock_then_make`. Với loại cuối, số thiếu được thể hiện thành phần cần in trước khi khách chấp thuận, không âm thầm đổi sau đặt hàng.

`BR-CAT-04`: SKU cho mọi biến thể; chế độ theo dõi `sku`, `lot` hoặc `serial` theo sản phẩm. Mã vạch/QR hỗ trợ nhập/xuất, kiểm kê, sản xuất, bảo hành. Serial duy nhất và có lịch sử trạng thái/vị trí.

### 4.2 File và quyền sở hữu

Sản phẩm vật lý có thể không kèm file. File là đối tượng số độc lập, có liên kết đến mẫu/sản phẩm và phiên bản tương ứng, không phải một cột đính kèm công khai. Cho mua file riêng, mua kèm, tải miễn phí theo quyền của từng file. Giá mua kèm có thể ưu đãi.

Nguồn thiết kế: tự thiết kế, thuê, mua giấy phép, file miễn phí được phép trên nền tảng khác. Hồ sơ bắt buộc khi áp dụng: chủ sở hữu/tác giả, URL nguồn, giấy phép và bản bằng chứng tại thời điểm nhận, thời hạn/phạm vi, yêu cầu ghi công. Tách riêng quyền in sản phẩm để bán, phân phối file và cấp cho người mua quyền in ra bán. Miễn phí không đồng nghĩa với có đủ các quyền này.

Giấy phép cá nhân/thương mại cấu hình theo file; điều khoản mặc định cấm bán/chia sẻ file gốc chỉ được dùng khi quyền nguồn cho phép. Không ghi đè điều khoản của giấy phép nguồn bằng điều khoản hẹp hơn trái phép. Mẫu dựa trên nhân vật/tác phẩm bên thứ ba cần kiểm tra quyền liên quan; mua file từ người dựng không tự chứng minh quyền đối với nhân vật.

### 4.3 Xuất bản và an toàn

`BR-CAT-05`: `draft → in_review → published`; có `rejected`, `paused`, `archived`. Kiểm tra giá, biến thể, media, nguồn quyền, thông tin sử dụng và dữ liệu sản xuất cần thiết. Duyệt hàng loạt vẫn phải ghi kết quả từng sản phẩm. Khi sửa thông tin nhạy cảm của bản đang bán, tạo bản nháp mới; không thay âm thầm chính sách đã áp dụng cho đơn.

Quản lý hướng dẫn, điều kiện sử dụng, giới hạn nhiệt, chăm sóc, cảnh báo điện/linh kiện/chi tiết nhỏ theo nhóm. Tuyên bố an toàn thủy sinh hoặc tính chất vật liệu phải có căn cứ. Nhóm cần kiểm chứng chưa đạt thì chưa mở bán, không dùng nội dung marketing thay hồ sơ kiểm tra.

### 4.4 Giá và khuyến mãi

Nhân viên quyết định giá. Hệ thống ước tính chi phí vật liệu, máy, nhân công, linh kiện, hậu xử lý, hao hụt và đóng gói; đối chiếu với thực tế sau sản xuất. Giá bán và cấu phần chi phí là hai dữ liệu độc lập. Không tự thay giá sản phẩm khi chi phí cập nhật.

Hỗ trợ giảm giá sản phẩm, mã giảm giá đơn, miễn/giảm phí vận chuyển, combo, mua vật lý kèm file; thời gian, đối tượng, sản phẩm, số lượng và tổng lượt dùng; giới hạn theo khách; quy tắc ưu tiên/cộng dồn. Phải tính lại trên server, giới hạn ngân sách và chống dùng trùng khi đặt đồng thời.

Mỗi đơn lưu bản chụp tên/SKU, giá, giảm giá, xu, tiền tệ, giấy phép, chính sách và thông tin pháp lý. Đổi giá hoặc chính sách chỉ tác động đơn mới, trừ thay đổi đơn đã được khách xác nhận.

## 5. Khám phá và trải nghiệm mua hàng

### 5.1 Ngôn ngữ thiết kế

Ý tưởng “những chiếc hộp nhỏ”: khối lập phương, hộp trưng bày, chiều sâu, tương tác mở hộp. Nền hiện đại tối giản, ưu tiên sản phẩm. Kết hợp CSS với cảnh 3D có chọn lọc ở trang chủ/bộ sưu tập; không phủ mọi trang bằng cảnh 3D nặng. Không bắt khách thao tác 3D để tìm kiếm hoặc thanh toán.

Sản phẩm có asset phù hợp được xoay/phóng to mô hình xem trước; dùng bản tối ưu riêng, tách khỏi file in. Có ảnh/video dự phòng và thừa nhận mô hình gửi xuống trình duyệt có thể bị trích xuất.

### 5.2 Responsive có hành vi riêng

| Thiết bị | Yêu cầu trải nghiệm |
|---|---|
| Mobile | Điều hướng dưới cho khu vực phù hợp, nút mua trong tầm tay, chọn biến thể/bộ lọc dạng sheet, checkout ít nhập liệu, hỗ trợ bàn phím ảo/safe area |
| Tablet | Bố cục hai vùng khi hữu ích, cảm ứng và bàn phím, ngang/dọc; không phóng to bản mobile một cách cơ học |
| Laptop | Điều hướng đầy đủ, danh sách và chi tiết cân đối, hỗ trợ bàn phím |
| Desktop lớn | Dùng không gian cho bộ lọc/dashboard nhưng giới hạn độ dài dòng, không kéo giãn nội dung vô hạn |

Admin có màn hình tác nghiệp responsive theo vai trò: quét mã, nhận hàng, QC, cập nhật sản xuất. Bảng nhiều cột cần chế độ thẻ/chi tiết hoặc chọn cột; không buộc nhân viên đọc bảng thu nhỏ. Chỉ xác nhận nghiệp vụ khi có mạng; giữ bản nháp an toàn khi có thể, hiển thị chưa lưu và thử lại chống trùng. Không hỗ trợ ghi nghiệp vụ offline trong giai đoạn đầu.

### 5.3 Tìm kiếm và tài khoản

Tìm có/không dấu, gợi ý, lỗi gõ phổ biến, tìm SKU chính xác; bộ lọc theo danh mục/giá/thuộc tính/có sẵn/cần in/có file; sắp xếp giá, mới, bán chạy, đánh giá. Không hiển thị bản nháp, file bị gỡ hoặc dữ liệu nội bộ qua tìm kiếm.

Khách mua không cần tài khoản. Đăng nhập bằng email/số điện thoại/username + mật khẩu, Facebook, Google. Liên kết danh tính phải xác minh, không gộp tự động chỉ vì provider trả cùng email. Quyền tải/đơn cũ gắn với xác minh email và claim đơn, không chỉ nhập mã đơn dễ đoán.

Số điện thoại chưa xác minh chỉ là thông tin liên hệ; đề xuất chưa cho dùng làm định danh đăng nhập cho đến khi có quy trình xác minh đáng tin cậy. SMS OTP chưa được chọn ở giai đoạn đầu; điểm này phải được quyết định ở bảng `OPEN`, không âm thầm xây tính năng đăng nhập không an toàn.

Danh sách yêu thích: tài khoản đồng bộ giữa thiết bị; khách chưa đăng nhập có thể lưu tạm trên thiết bị (đề xuất). Báo có hàng theo biến thể; khách vãng lai xác minh email, có hủy đăng ký; hàng còn quá ít phải kiểm tra tồn khi mua, email không phải cam kết giữ hàng.

## 6. Đơn hàng, tiền và giao tách

### 6.1 Quy trình chung

1. Khách chọn biến thể, số lượng, file/giấy phép, phương án giao và địa chỉ; nhận báo giá có thời hạn.
2. Server tính giá, ưu đãi/xu, khả dụng, phần in, phí và thời gian dự kiến; khách xác nhận tổng và chính sách.
3. Tạo đơn cùng bản chụp điều kiện và kế hoạch thanh toán; giữ tồn và xu có thời hạn. Không hiện “đã xác nhận” khi còn thất bại giữ nguồn lực.
4. Hàng có sẵn: xử lý xác nhận/COD hoặc thu trước. Hàng cần in: nhân viên duyệt khả năng/lịch trước rồi gửi yêu cầu cọc.
5. Khi đủ cọc của phần cần in mới phát hành công việc sản xuất. File được thanh toán đủ có thể mở tải riêng.
6. QC, phân bổ thành phẩm, đóng gói, chọn hãng, tạo vận đơn, theo dõi giao và đối soát.
7. Hoàn tất từng dòng/đợt và đơn; xử lý hậu mãi, xu chờ, hóa đơn theo nghiệp vụ áp dụng.

### 6.2 Phê duyệt và thời gian

Khách thấy ước tính từ định mức, hàng đợi, năng lực máy, vật liệu và lịch làm việc; có khoảng dự phòng khi thiếu dữ liệu. Hiển thị riêng sản xuất/vận chuyển. Nhân viên xác nhận lịch rồi yêu cầu cọc; thay đổi lịch ảnh hưởng cam kết cần thông báo/chấp thuận. Không hứa lịch máy chưa giữ như một cam kết chắc chắn.

Hệ thống đề xuất farm/kho và lý do: tồn khả dụng, tương thích máy/vật liệu, hàng đợi, địa chỉ, thời gian. Nhân viên xác nhận/điều chỉnh. Thiếu hàng sau đặt: đề xuất in, đổi biến thể, giao phần có hoặc hủy phần thiếu; chờ khách đồng ý mọi thay đổi giá/cọc/lịch.

### 6.3 Các chiều trạng thái

| Đối tượng | Trạng thái cốt lõi |
|---|---|
| Đơn hàng | `pending_confirmation`, `awaiting_customer`, `confirmed`, `processing`, `partially_fulfilled`, `fulfilled`, `completed`, `cancelled`, `closed` |
| Thu tiền | `unpaid`, `partially_paid`, `paid`, `refund_pending`, `partially_refunded`, `refunded`; có ngoại lệ đối soát |
| Yêu cầu in | `awaiting_review`, `awaiting_deposit`, `ready`, `scheduled`, `printing`, `post_processing`, `qc`, `completed`, `blocked`, `cancelled` |
| Giao hàng | `planned`, `packed`, `awaiting_pickup`, `in_transit`, `delivered`, `delivery_failed`, `returning`, `returned`, `lost`, `cancelled` |
| Hậu mãi | Yêu cầu trả/hoàn/bảo hành có trạng thái và phê duyệt riêng |

Đơn không dùng một trạng thái duy nhất để suy ra tất cả. Giao thành công không đồng nghĩa hãng đã trả COD. Hủy một dòng không được hủy các phần đã hoàn tất. Tất cả trạng thái có người/hệ thống thực hiện, thời gian, lý do và phiên bản.

### 6.4 Nguyên tắc phân bổ tiền

VND là tiền giao dịch ban đầu. Tiền được làm tròn theo đơn vị tiền tệ; quy tắc phân bổ phần dư xác định và lưu trên từng dòng.

`Tiền hàng thực trả = tiền hàng − giảm giá phân bổ − giá trị Minixu sử dụng`.

`Tổng khách phải trả = tổng tiền hàng thực trả + phí vận chuyển khách chịu + khoản hợp lệ được công bố`.

Thuế được cấu hình sau xác minh pháp lý; không mặc định cộng VAT hoặc mặc định xuất hóa đơn chỉ khi khách yêu cầu. Giá hiển thị và tổng phải minh bạch theo chế độ áp dụng.

Đề xuất cơ sở cọc: tỷ lệ trên tiền hàng thực trả của phần cần in, không gồm file/phí vận chuyển. Một khoản chuyển vào phải được phân bổ cho nghĩa vụ cụ thể: file, cọc, dư hàng sẵn, dư hàng in, phí giao. Không dùng cùng khoản tiền để mở file và coi như đủ cọc.

Ví dụ minh họa, không phải giá/chính sách được duyệt: hàng sẵn 200.000, hàng cần in 300.000, file 50.000, phí giao 30.000, không ưu đãi; cọc đề xuất 50%. Trả 200.000 được phân bổ 50.000 cho file + 150.000 cọc; số dư 380.000. Nếu tách giao, tổng COD của các kiện và các khoản thu thêm không được vượt số dư; việc thu phí giao theo từng kiện phải thể hiện trong báo giá.

Mặc định giao chung, khách có thể chọn giao tách với giá và thời gian riêng. File không chờ kiện vật lý. Khách chọn phương án giao, Minibox chọn GHN/GHTK/SPX theo khả dụng và nhân viên xác nhận. Đổi hãng không tự tăng khoản khách phải trả. Phụ phí thực tế lệch báo giá được ghi chi phí; thu thêm chỉ khi có căn cứ và khách chấp thuận.

### 6.5 Giữ hàng, hạn thanh toán và ngoại lệ

Giữ tồn có thời hạn theo phương thức và bước duyệt; hết hạn giải phóng. Đơn hỗn hợp cần mốc giữ xuyên bước duyệt/cọc; gia hạn có lý do. Kho không bán âm, không giữ hàng cách ly hoặc đang điều chuyển như đã nhận.

Hết hạn nhưng tiền đến sau: ghi nhận tiền thật vào tài khoản chờ xử lý, không tự khởi động lại đơn hoặc lấy tồn của người khác. Nhân viên đề nghị tiếp tục nếu còn khả năng hoặc hoàn tiền. Chuyển thiếu/ thừa/ sai nội dung/ trùng đều có hàng đợi đối soát.

VietQR là cách tạo thông tin chuyển khoản; xác nhận tự động cần nhà cung cấp dữ liệu ngân hàng có kết nối thực tế. Ảnh chụp giao dịch không đủ làm bằng chứng tự động tiền đã vào. COD chỉ ghi nhận theo bằng chứng thu/giao và đối soát riêng khoản hãng phải trả.

## 7. Hủy, trả hàng, hoàn tiền và bảo hành

`BR-AFT-01`: trước khi sản xuất bắt đầu, hủy phần cần in được hoàn toàn bộ cọc liên quan. Sau bắt đầu, xét duyệt chi phí thực đã phát sinh với bằng chứng; không khấu trừ tùy ý vượt chính sách đã chấp thuận. Nếu Minibox không thực hiện được hoặc trễ cam kết và khách không nhận lịch mới, hoàn khoản đã thu cho phần hủy.

`BR-AFT-02`: trả hàng lỗi, hỏng, giao sai; đổi ý chỉ hàng có sẵn đủ điều kiện. Hàng in theo mẫu vẫn được xử lý chất lượng; “in theo đơn” không miễn nghĩa vụ áp dụng. Thời hạn cụ thể là `PROPOSED`.

`BR-AFT-03`: file chưa tải được yêu cầu hoàn; sau lần tải đầu xét file lỗi/sai mô tả/không có quyền cung cấp, ưu tiên sửa/thay phù hợp. Không hoàn do đổi ý sau tải theo định hướng đã chốt, nhưng phải rà soát pháp luật áp dụng. Khi hoàn, thu hồi tải tiếp và cập nhật; không tuyên bố xóa bản khách đã có.

`BR-AFT-04`: yêu cầu → bằng chứng → xét duyệt → nhận/kiểm hàng nếu cần → xác định phân bổ hoàn → chuyển khoản thủ công → lưu bằng chứng → đối chiếu/đóng. Duyệt hoàn không tự có nghĩa đã chi tiền. Hỗ trợ một phần; ngăn hoàn trùng, hoàn vượt tiền đã thu hoặc vượt số lượng có thể trả. Thông tin nhận hoàn được xác minh; thay tài khoản nhận cần audit/xác thực lại.

Hoàn tiền thật và hoàn xu là hai nghiệp vụ riêng. Ưu đãi/xu được phân bổ theo dòng tại lúc mua; không tính hoàn theo giá niêm yết. Không tự truy thu ưu đãi combo đã dùng nếu điều kiện đó chưa được khách chấp thuận. Phí giao/chi phí trả xử lý theo nguyên nhân và chính sách áp dụng.

`BR-AFT-05`: hàng trả và hàng lỗi vào khu vực cách ly, không lập tức tăng tồn bán được. Kết quả: nhập lại, sửa, in lại, thu hồi linh kiện, loại B, tiêu hủy. Loại B có mô tả tình trạng, giá, chính sách riêng và duyệt xuất bản.

`BR-AFT-06`: bảo hành theo sản phẩm/nhóm; snapshot tại lúc mua, quản lý theo đơn/serial. Tiếp nhận, xác minh thời hạn/phạm vi, kiểm tra, sửa/thay linh kiện/đổi và giao lại. Không dùng bảo hành để xóa yêu cầu trả hàng hợp lệ. Chính sách riêng không loại bỏ nghĩa vụ bắt buộc.

## 8. Minixu

Minixu là điểm thưởng dùng trong Minibox theo thiết kế nghiệp vụ, không nhận nạp tiền, không đổi tiền mặt. Không xây chức năng chuyển xu giữa khách ở phạm vi đầu (đề xuất). Việc gọi giao diện là “ví” không tự xác định phân loại pháp lý; cần rà soát chương trình thực tế trước phát hành.

| Mã | Quy tắc |
|---|---|
| `BR-XU-01` | Cả hàng vật lý và file trả phí được tích/dùng; có loại trừ theo sản phẩm/chương trình; file miễn phí không thưởng |
| `BR-XU-02` | Tích trên tiền hàng thực trả sau giảm giá và trừ xu; không gồm phí giao/phần hoàn; không tính từ tiền cọc như đơn hoàn tất |
| `BR-XU-03` | Xu chờ đến khi đơn hoàn tất và hết thời hạn trả thông thường; khiếu nại đang mở giữ phần liên quan; có lịch khả dụng cho file được cấu hình |
| `BR-XU-04` | Mỗi đợt xu có hạn riêng từ ngày khả dụng; nhận mới không gia hạn cũ; dùng lô sắp hết hạn trước |
| `BR-XU-05` | Nhắc xu gần hết hạn bằng email và trong tài khoản; gộp thông báo, chống gửi lặp |
| `BR-XU-06` | Mức dùng tối đa theo tỷ lệ tiền hàng sau giảm giá và trần; không dùng cho phí giao; giới hạn không vượt tiền của dòng đủ điều kiện |
| `BR-XU-07` | Đặt hàng giữ xu có thời hạn; xác nhận thì ghi tiêu; hủy/không hoàn tất thì giải phóng hoặc hoàn theo trạng thái; không trừ hai lần |
| `BR-XU-08` | Hoàn xu đã dùng theo phần hàng hoàn; giữ hạn gốc, thêm khoảng gia hạn tối thiểu nếu cần; không đổi thành tiền |
| `BR-XU-09` | Thu hồi xu thưởng tương ứng phần hoàn, độc lập xu dùng được hoàn; nếu đã tiêu, ghi nghĩa vụ khấu trừ xu tương lai, không tự tạo khoản nợ tiền (đề xuất) |
| `BR-XU-10` | Đơn guest ghi xu chờ theo đơn; claim sau xác minh và liên kết trong hạn; một đơn nhận một lần; đăng nhập mới dùng xu |

Chính sách giữ xu sắp hết hạn, khoảng gia hạn khi đơn thất bại và thời điểm hoàn tất đơn số cần cấu hình rõ. Đề xuất hold không quá hạn lô; khi báo giá hết hạn phải tính lại, không âm thầm tăng số tiền khách phải trả.

Giao diện hiển thị khả dụng, đang giữ, chờ nhận, sắp hết hạn và lịch sử. Sổ xu lưu nguồn đơn/hoàn/chương trình, thời hạn, người thực hiện, lý do; không sửa số dư trực tiếp.

Giai đoạn sau có thể thêm thẻ lưu sẵn cùng khu vực ví. Sổ xu và phương thức thanh toán tách biệt; thẻ trả đơn, không nạp xu. Dùng token của nhà cung cấp, không lưu CVV; phương án tích hợp và tuân thủ phải được đánh giá riêng.

## 9. Farm, BOM và sản xuất

`BR-MFG-01`: FDM và resin có loại máy, vật liệu, thông số, quy trình hậu xử lý riêng. Thông số kỹ thuật từ slicer/định mức và báo cáo nhân viên; chưa có kết nối máy trực tiếp. Không suy ra giờ chạy thực từ lịch dự kiến.

`BR-MFG-02`: BOM theo biến thể gồm chi tiết in, vật tư, linh kiện mua ngoài, lắp ráp; routing gồm công đoạn và QC. BOM/routing có phiên bản, hiệu lực. Lệnh đã phát hành giữ snapshot, không đổi khi sửa định mức; thay thế vật tư cần duyệt tương thích.

`BR-MFG-03`: công việc có thể gom thành mẻ nhiều đơn hoặc bổ sung kho. Lưu chi tiết nhu cầu, số lượng, farm/máy, lịch, lô/cuộn/chai, định mức/thực dùng, người thao tác. Thành phẩm chỉ phân bổ trong giới hạn nhu cầu và số lượng đạt, không ghi một chiếc cho hai đơn.

`BR-MFG-04`: luồng: duyệt/đủ cọc → cấp vật tư → lịch máy → in → hậu xử lý → lắp ráp → QC → nhập thành phẩm/phân bổ → đóng gói. Các bước không áp dụng có thể bỏ theo routing đã duyệt, không bỏ QC bắt buộc.

`BR-MFG-05`: lỗi theo nguyên nhân, giai đoạn, lượng hao, ảnh; sửa/in lại tạo công việc liên kết, không tăng số lượng khách mua hoặc tự thu thêm. Thành công một phần ghi theo số lượng. Chi phí phế phẩm, in lại phân bổ có chính sách để không che lợi nhuận thực.

`BR-MFG-06`: QC checklist theo nhóm và phiên bản; kết quả theo mẻ/từng chiếc/serial, đo lường và ảnh khi cần. Chỉ đạt mới vào tồn sẵn sàng. Bất đồng QC được duyệt lại có lịch sử, không sửa mất kết quả cũ.

`BR-MFG-07`: bảo trì theo ngày/giờ chạy, sự cố/sửa chữa, phụ tùng/chi phí. Máy dừng không có năng lực khả dụng; cảnh báo công việc và lịch giao ảnh hưởng. Nhân viên điều phối xác nhận chuyển máy/lịch mới.

Giá thành dự kiến và thực tế gồm nhựa, linh kiện, nhân công, giờ máy, hậu xử lý, phế phẩm/hao hụt và vật tư đóng gói theo chính sách. Chưa tuyên bố đây là giá thành kế toán pháp định.

## 10. Kho và mua hàng

Farm và kho là đối tượng độc lập; liên kết nhiều địa điểm theo nhu cầu. Kho có khu/bin cho nguyên liệu, thành phẩm, cách ly, hàng loại B. Không nhầm địa điểm sản xuất với kho đang sở hữu tồn.

Tồn gồm đang có, đã giữ, khả dụng, cách ly, đang điều chuyển. Lô/serial/cuộn/chai có lượng đầu, còn lại, đơn vị chuẩn, hạn nếu có, vị trí và lịch sử cấp/hoàn vật tư. Mua theo cuộn/chai nhưng tiêu hao theo g/ml khi đúng vật liệu; không quy đổi khối lượng/thể tích bằng hệ số giả định chung.

Điều chuyển: yêu cầu → duyệt → xuất nguồn → đang chuyển → nhận đích → xác nhận chênh lệch. Xuất nguồn không lập tức cộng đích. Hỗ trợ nhận từng phần, mất/hỏng, ảnh và phê duyệt điều chỉnh. Kiểm kê có snapshot/cutoff và xử lý giao dịch trong lúc đếm, không ghi đè số đếm vào tồn mà bỏ giao dịch mới.

Mua hàng: nhà cung cấp → đề nghị/đơn mua → duyệt → giao/nhận từng phần → QC → nhập → hóa đơn/chi phí nguồn → công nợ/thanh toán → đóng. Có trả nhà cung cấp, giảm công nợ/nhận hoàn, hạn thanh toán; tổng nhận/trả/thanh toán đối chiếu theo dòng.

Bổ sung tồn: ngưỡng min/max, tồn khả dụng, nhu cầu, hàng đang sản xuất/mua/điều chuyển, tốc độ bán → đề xuất → nhân viên duyệt → lệnh sản xuất hoặc yêu cầu mua. Không tạo trùng đề xuất đang mở.

Đóng gói: quy cách theo sản phẩm/nhóm, xác nhận từng kiện, đủ hàng/phụ kiện, vật tư, cân đo thực tế, ảnh hàng dễ vỡ. Theo dõi kiện–nội dung–vận đơn; nếu hãng chỉ hỗ trợ một kiện/vận đơn phải tách theo khả năng thật.

## 11. Tài chính và hóa đơn

Tài chính vận hành gồm thu/chi, cọc, số dư, hoàn, công nợ nhà cung cấp, khoản COD hãng còn giữ, phí giao, đối soát và báo cáo lợi nhuận. Không thay thế sổ kế toán/tờ khai/báo cáo pháp định. Chưa có phần mềm kế toán; xuất dữ liệu và chuẩn bị adapter sau.

Phân biệt doanh thu được ghi nhận, tiền khách thanh toán, tiền ngân hàng thực nhận và tiền COD đang chờ. Cọc không tự là doanh thu. Chính sách ghi nhận báo cáo phải được duyệt; không gộp giá trị xu với tiền thật. Thu/chi và điều chỉnh có chứng từ, phê duyệt và kỳ đối soát.

Hóa đơn điện tử: provider chưa chọn. Quản lý dự thảo, gửi, chấp nhận/phát hành, thất bại, xử lý sai sót theo quy định/provider; mã tra cứu và bản liên quan. Không mặc định “chỉ xuất khi khách yêu cầu” hoặc “chỉ xuất khi đơn hoàn tất”: thời điểm, loại hóa đơn, thuế, ký số, điều chỉnh/thay thế phải được người có chuyên môn xác nhận theo hộ kinh doanh/công ty lúc vận hành. Gửi trùng/timeout phải tra cứu trước khi phát hành lại.

Khi đổi pháp nhân, lưu lịch hiệu lực, tài khoản ngân hàng/hợp đồng/provider theo chủ thể; đơn cũ có snapshot, xử lý hoàn/hóa đơn theo chủ thể liên quan. Không đổi hàng loạt tên/mã số thuế trên lịch sử.

## 12. Nội dung, tương tác và chăm sóc khách hàng

- CMS trong admin: bài viết, chuyên mục, thẻ, tác giả, thư viện media, nháp/duyệt/hẹn giờ, SEO; banner/menu/trang chính sách; gắn sản phẩm/bộ sưu tập; sẵn cấu trúc bản dịch.
- Đánh giá: chỉ mua đủ điều kiện, 1–5 sao, nội dung, ảnh/video, nhãn đã mua, phản hồi shop; đăng tự động, báo cáo/kiểm duyệt. Không ẩn chỉ vì điểm thấp; lý do xử lý và lịch sử phải lưu.
- Hỏi đáp sản phẩm/bình luận blog: đăng nhập, không bắt buộc mua; phản hồi chính thức, chống spam/báo cáo. Nhân viên không được giả đánh giá khách.
- Hỗ trợ: ticket gắn đơn/sản phẩm, ảnh/file an toàn, người phụ trách, ưu tiên, trạng thái, trao đổi công khai với khách và ghi chú nội bộ tách biệt. Đổi người phụ trách không mất lịch sử.
- Thông báo đầu kỳ: email và trong tài khoản, gồm giao dịch/hỗ trợ/xu sắp hết hạn; báo có hàng do khách đăng ký. Chưa newsletter, quảng cáo, nhắc giỏ bỏ quên, Zalo/SMS hoặc chat realtime.

## 13. Admin và báo cáo

Điều hướng gồm ba vùng rõ ràng: nghiệp vụ; cài đặt hệ thống/chính sách; kỹ thuật/tích hợp. Không đưa trạng thái kỹ thuật không cần thiết vào trải nghiệm khách mua.

Dashboard theo quyền và vai trò: doanh thu, tiền thực thu, đơn cần xử lý, sản xuất trễ, máy dừng, hàng thấp, yêu cầu hậu mãi, công nợ đến hạn, COD lệch và cảnh báo tài chính. Bộ lọc thời gian/kênh/kho/farm; so sánh kỳ; bấm vào chỉ số mở danh sách tạo nên chỉ số đó.

| Nhóm | Nội dung và định nghĩa tối thiểu |
|---|---|
| Bán hàng | Đơn đặt/xác nhận/giao, doanh số gộp/ròng, giảm giá, trả/hoàn; tránh đếm mỗi kiện thành một đơn |
| Tiền | Tiền thu thật, cọc còn giữ, COD phải thu, tiền hoàn đã chi, ngoại lệ đối soát |
| Lợi nhuận | Dự kiến vs thực tế, COGS/chi phí vận hành/phí kênh tách rõ; dữ liệu thiếu có nhãn chưa đầy đủ |
| Kho/mua | On-hand/khả dụng/cách ly/chuyển, tuổi tồn, hao hụt, lead time nhà cung cấp, công nợ |
| Farm/máy | Tiến độ, giờ máy thực/dự kiến, tỷ lệ đạt/lỗi, in lại, hao vật tư, downtime |
| Khách/file | Mua lại, doanh số vật lý/file, giấy phép, tải/cập nhật; không coi lượt tải là doanh số |
| Minixu | Đã cấp/chờ/giữ/tiêu/hết hạn/hoàn/thu hồi, giá trị quy đổi theo phiên bản chính sách |

Xuất CSV/XLSX có phân quyền, tác vụ nền, hạn tải và audit. Thời gian báo cáo theo `Asia/Ho_Chi_Minh` mặc định; có timestamp độ mới. Không cộng trực tiếp nhiều tiền tệ trong báo cáo tương lai.

## 14. Bộ thông số mặc định đề xuất — chờ PO duyệt

Các giá trị dưới đây chỉ phục vụ thiết kế/demo, không phải cam kết đã được PO hoặc luật sư duyệt. Admin có lịch hiệu lực và snapshot trên giao dịch; không thay hồi tố.

| ID | Tham số | Giá trị đề xuất | Ghi chú |
|---|---|---|---|
| CFG-01 | Giá trị dùng 1 Minixu | 1 VND giảm tiền hàng | Không phải quyền đổi tiền mặt; chỉ VND đầu kỳ |
| CFG-02 | Tỷ lệ thưởng | 1% tiền hàng thực trả | Làm tròn xuống số xu nguyên; tỷ lệ riêng theo chương trình |
| CFG-03 | Mức dùng xu | Tối đa 20% tiền hàng đủ điều kiện sau giảm giá | Trần 100.000 xu/đơn; không vượt số dư khả dụng |
| CFG-04 | Hạn xu | 180 ngày từ khả dụng | Theo từng lô |
| CFG-05 | Nhắc hết hạn | Trước 14, 7 và 1 ngày | Gộp theo khách/ngày, chỉ số xu còn lại |
| CFG-06 | Gia hạn xu hoàn | Ít nhất 30 ngày từ ngày hoàn | Hạn mới = max(hạn gốc, ngày hoàn + 30 ngày) |
| CFG-07 | Claim xu đơn guest | 30 ngày từ đơn hoàn tất | Sau claim vẫn chờ đủ điều kiện trả hàng |
| CFG-08 | Thu hồi thưởng đã tiêu | Khấu trừ thưởng khả dụng/tương lai | Không thu tiền, cần điều khoản và audit |
| CFG-09 | Cọc hàng cần in | 50% tiền hàng thực trả của phần cần in | Có override sản phẩm; không gồm file/phí giao |
| CFG-10 | Trả số dư | Khách chọn trả trước hoặc COD | Nếu chọn trả trước: hạn 48 giờ sau báo sẵn sàng |
| CFG-11 | Giữ đơn chuyển khoản hàng sẵn | 30 phút sau tạo yêu cầu thanh toán | Tiền đến muộn vào đối soát |
| CFG-12 | Xác nhận COD | Trong 24 giờ | Hết hạn cần giải phóng/cancel theo quy trình có thông báo |
| CFG-13 | Duyệt hàng cần in | Mục tiêu 1 ngày làm việc | Cọc trả trong 24 giờ sau duyệt; giữ tồn hàng sẵn kèm đơn đến hết mốc này nếu đã được duyệt gia hạn |
| CFG-14 | Trả vì đổi ý hàng sẵn | 7 ngày từ giao thành công | Còn nguyên điều kiện bán; khách chịu phí nếu chính sách hợp lệ |
| CFG-15 | Lỗi/hỏng/giao sai | Tiếp nhận thông thường trong 7 ngày | Không dùng mốc này loại trừ quyền bắt buộc/bảo hành sau đó; Minibox chịu phí khi lỗi thuộc mình |
| CFG-16 | Khả dụng thưởng vật lý | Sau mốc trả hàng thông thường và hoàn tất đơn | Có tranh chấp thì giữ phần liên quan |
| CFG-17 | Khả dụng thưởng file | 7 ngày sau cấp quyền và hoàn tất đơn | Mốc thưởng riêng; không tự coi quyền khiếu nại hết sau 7 ngày |
| CFG-18 | Phản hồi yêu cầu hậu mãi | 1 ngày làm việc | Chưa phải cam kết 24/7 |
| CFG-19 | Thực hiện hoàn đã duyệt | 3–5 ngày làm việc | Sau xác minh người nhận và đủ hồ sơ |
| CFG-20 | Bảo hành riêng | Bắt buộc chọn theo nhóm, chưa đặt chung | Thiết bị điện/linh kiện cần duyệt riêng; không tự suy ra nghĩa vụ |
| CFG-21 | Quyền tải | Link 5 phút, xác minh email 10 phút | Rate limit thích ứng, không giới hạn tổng lượt tải bình thường |
| CFG-22 | Kết hợp ưu đãi | 1 mã đơn + giảm sản phẩm + xu nếu chương trình cho phép | Không cộng vô hạn; ưu đãi vận chuyển có ngân sách riêng |
| CFG-23 | Phê duyệt thu/chi/điều chỉnh | Mọi hoàn tiền và chi tiền cần chủ shop duyệt lúc đầu | Ngưỡng chi tiết chưa chốt; chưa bật tự duyệt |
| CFG-24 | Đơn hoàn tất | Đã thực hiện/giải quyết mọi dòng, đủ thanh toán hoặc có điều chỉnh hợp lệ | COD đối soát hãng theo dõi riêng; hủy toàn bộ không thưởng |
| CFG-25 | Giờ làm việc cho SLA | Cấu hình theo lịch farm/shop | Chưa giả định làm cuối tuần/ngày lễ |

## 15. Mốc triển khai và điều kiện mở bán đề xuất

| Mốc | Phạm vi | Bằng chứng nghiệm thu |
|---|---|---|
| M0 — Nền tảng | Repo, môi trường, schema/role, auth admin, CI, backup thử, design system, hợp đồng mẫu | CI chạy thật, migration trên DB sạch và nâng cấp, kiểm tra quyền chéo schema, demo responsive |
| M1 — Danh mục và cửa hàng | SKU/biến thể, giá, quyền thiết kế, media, tìm kiếm, tài khoản/guest, trang sản phẩm, giỏ hàng | Luồng tìm/chọn/đặt chạy trên các thiết bị; bản nháp/private file không lộ |
| M2 — Giao dịch | Đơn hỗn hợp, thu cọc/file/COD, VietQR, giữ kho/xu, khuyến mãi cốt lõi, giấy phép/tải, hoàn thủ công | Kịch bản chống trùng, chậm/thiếu tiền, hết tồn và claim guest; tiền/xu cân đối |
| M3 — Sản xuất và giao hàng | BOM FDM/resin, mẻ, vật tư, QC, kho/điều chuyển, đóng kiện, GHN/GHTK; SPX nếu được cấp quyền | Đơn thực nghiệm đi hết sản xuất–giao–COD–trả; kiểm tra lỗi/in lại/thiếu hàng |
| M4 — Cổng mở bán | Hậu mãi/bảo hành cốt lõi, thông báo, Minixu đầy đủ, tài chính cơ bản, hóa đơn, dashboard, pháp lý và DR | Tất cả điều kiện bên dưới đạt; PO duyệt mở bán theo bằng chứng |
| M5 — Hoàn thiện vận hành | Mua hàng/công nợ đầy đủ, bảo trì, bổ sung tồn, giá thành thực, phê duyệt nâng cao, báo cáo đầy đủ | Từng BR và quy trình ngoại lệ được nghiệm thu, không chỉ màn hình |
| M6 — Hoàn thiện giai đoạn đầu | CMS đầy đủ, cộng đồng, combo nâng cao, wishlist/báo có hàng, ticket nâng cao, 3D chọn lọc, SPX còn chờ | Đối chiếu toàn bộ ma trận, không còn yêu cầu giai đoạn đầu bị bỏ sót |

M4 là đề xuất mốc mở bán giới hạn: chỉ mở sản phẩm/kênh đã được chứng minh quy trình. Những phần dời M5/M6 vẫn là cam kết giai đoạn đầu. Không quảng cáo tính năng chưa bật. Nhận diện khối hộp/mobile phải có từ M1; M6 bổ sung cảnh 3D thực và chiều sâu nội dung, không trì hoãn yêu cầu responsive.

Điều kiện bắt buộc mở bán:

1. PO duyệt bộ CFG, phạm vi sản phẩm/nhóm mở, giới hạn vận hành và điều khoản.
2. Có chủ thể kinh doanh, thông tin pháp lý, quyền thiết kế và quy trình thuế/hóa đơn phù hợp; xác minh thủ tục website bán hàng tại thời điểm mở bán.
3. Nhà cung cấp ngân hàng, email, vận chuyển và hóa đơn có tài khoản/quyền thật; chứng minh luồng cần dùng. Có mock/sandbox chưa đủ.
4. Không còn lỗi nghiêm trọng về tiền/xu, oversell, quyền truy cập, private file, bảo mật đăng nhập hoặc mất dữ liệu.
5. Hoàn thành đơn hỗn hợp, giao tách, hoàn một phần, hủy cọc và file; đối soát tiền/xu/kho bằng bằng chứng.
6. Sao lưu ngoài máy, diễn tập RPO ≤ 1 giờ và RTO 4–8 giờ với dữ liệu đại diện; có người chịu trách nhiệm xử lý sự cố.
7. Kiểm tra mobile/tablet/laptop/desktop lớn và thiết bị thật; 3D lỗi không chặn mua hàng.
8. Có phương án ngừng nhận đơn khi mất dịch vụ trọng yếu và xử lý thủ công có audit; không làm giả xác nhận thành công.

## 16. Những việc còn cần xác minh, không hỏi lại toàn bộ khám phá

| ID | Điểm mở | Người/điều kiện quyết định |
|---|---|---|
| OPEN-01 | Phê duyệt bảng CFG và mốc M4 | PO duyệt một lần, có thể chỉnh từng dòng |
| OPEN-02 | CPU/RAM/SSD, đường truyền, IP public/CGNAT, UPS | Kiểm tra homeserver trước chọn cấu hình cuối |
| OPEN-03 | Nơi sao lưu ngoài nhà và ngân sách duy trì | PO chọn sau báo giá; không có backup ngoài máy thì chưa đạt DR |
| OPEN-04 | Provider VietQR/dữ liệu ngân hàng, email, hóa đơn | So sánh tính năng/chi phí, hợp đồng, sandbox và production |
| OPEN-05 | Tài khoản/API GHN, GHTK, SPX | Đặc biệt SPX chưa xác minh quyền tài khoản Minibox |
| OPEN-06 | Chính sách thuế, hóa đơn, dữ liệu cá nhân, tiêu dùng, Minixu, bản quyền | Rà soát chuyên môn trước phát hành, không tự suy luận từ chức năng phần mềm |
| OPEN-07 | Xác minh số điện thoại cho đăng nhập khi chưa dùng SMS | Chọn provider/kênh xác minh hợp lệ hoặc để phương thức này tắt có công bố đến khi đủ điều kiện |
| OPEN-08 | Logo, bảng màu, font, asset 3D mẫu | Người triển khai đề xuất theo bản sắc khối lập phương; PO duyệt thiết kế mẫu |
| OPEN-09 | Hạn/điều kiện bảo hành cụ thể theo nhóm | PO và người có chuyên môn sản phẩm duyệt |

Không cần tiếp tục hỏi từng thư viện hoặc từng trường dữ liệu: người triển khai được chủ động theo đặc tả kỹ thuật. Điểm mở ảnh hưởng tiền, pháp lý, quyền hoặc cam kết khách phải giữ trạng thái chờ, không đoán để mở production.

## 17. Ma trận truy vết quyết định khám phá

| Câu | Nội dung được giữ | Phần áp dụng |
|---|---|---|
| 1–7 | Bên bán duy nhất, stock/in theo mẫu, file miễn phí/có phí, nguồn/quyền, VN trước/quốc tế sau, bán lẻ | 1, 4 |
| 8–12 | Guest, cọc theo tỷ lệ, COD/trả trước số dư, giao chung/tách | 5–6 |
| 13–20 | Máy/vật tư, farm/kho độc lập, đề xuất phân bổ, FDM/resin, BOM, giá/chi phí, mua hàng, cuộn/chai | 4, 9–10 |
| 21–25 | Tài chính vận hành, VietQR, tích hợp trực tiếp GHN/GHTK/SPX, Minibox chọn hãng | 6, 11 |
| 26–32 | Trả/hủy/cọc/hoàn thủ công, hộ kinh doanh → công ty, hóa đơn mở, RBAC và phê duyệt | 3, 7, 11 |
| 33–35 | Email/phone/username/password + FB/Google, email/in-app, danh mục/thuộc tính | 4–5, 12 |
| 36–42 | Khuyến mãi đầy đủ, Minixu và thẻ sau, chờ xu, hạn/mức dùng/tích/hoàn/guest | 4, 8, 14 |
| 43–49 | Đánh giá, hỏi đáp/bình luận, CMS, search, ticket, bảo hành, SKU/lot/serial | 4–5, 7, 12 |
| 50–54 | Mọi cập nhật file miễn phí, signed download, thu đủ file, hoàn file, đơn admin | 1, 4–7 |
| 55–57 | Wishlist/báo hàng, chưa hạng thành viên, báo cáo đầy đủ | 5, 13 |
| 58–67 | Quy mô, homeserver/Ubuntu, monorepo, 3 môi trường, Compose, GitHub Free, DR, mốc, MFA | 1, 3, 15–16 và đặc tả kỹ thuật |
| 68–74 | UI khối hộp/3D, viewer, admin/menu, thiết bị/offline, chủ động kỹ thuật, app-like mobile | 5, 13 |
| 75–85 | ETA, duyệt trước cọc, hold, thiếu hàng, an toàn, xuất bản, mẻ, bổ sung, bảo trì, QC, đóng kiện | 4, 6, 9–10 |
| 86–91 | Bảng mặc định, đề xuất mở bán, không marketing, cách ly/loại B, xu cho cả hai, hai Markdown | 7–8, 12, 14–16 |

## 18. Hướng dẫn sử dụng tài liệu để triển khai

Mỗi công việc triển khai phải chỉ rõ mã BR/CFG hoặc mục nghiệp vụ, dữ liệu bị tác động, tiêu chí chấp nhận và bằng chứng. Màn hình đẹp không thay thế luồng hoạt động; test local không thay thế nghiệm thu provider thật. Không seed dữ liệu demo vào production. Các chức năng `LATER` không được bật chỉ vì adapter có sẵn.

Sau mỗi mốc, cập nhật trạng thái từng yêu cầu và các điểm mở; PO nhận danh sách đã kiểm chứng, còn giả lập, còn phụ thuộc. Chỉ bắt đầu mốc tiếp theo sau khi lưu kết quả và xử lý lỗi chặn của mốc trước.
