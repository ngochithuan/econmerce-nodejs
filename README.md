# econmerce-nodejs

# Summary

Website E-commerce **chỉ bán máy tính và linh kiện máy tính**, backend Node.js + Javascript (Express.js), frontend tuỳ chọn.

- Customer (6đ): xem, tìm, lọc, sắp xếp sản phẩm, giỏ hàng realtime, checkout không cần đăng nhập, discount code, loyalty points, review và rating realtime
- Admin (2đ): dashboard, quản lý sản phẩm, user, order và discount code, **không thêm tính năng ngoài đề**
- Other (2đ): UI/UX, responsive, horizontal scaling, teamwork trên GitHub (ít nhất 1 tháng, mỗi người ít nhất 2 commits/tuần)
- Deploy bằng public hosting hoặc Docker Compose (chạy được chỉ với `docker compose up -d`)
- Bonus tối đa 2đ: CI/CD, microservices, AI features, ElasticSearch

# Todo List

## Setup

- [ ] Khởi tạo project Node.js + Express.js, chọn frontend framework
- [ ] Thiết kế database (users, addresses, products, variants, categories, tags, carts, orders, order status history, reviews, ratings, discount codes, loyalty points)
- [ ] Seed đủ data để demo pagination, mỗi sản phẩm có ít nhất 2 variants, 3 hình ảnh, description ít nhất 5 dòng
- [ ] Tạo sẵn account admin và account customer có data để chấm

## Customer Features

- [ ] Landing page: New Products, Best Sellers, ít nhất 3 category khác
- [ ] Register (email, full name, shipping address) và Login
- [ ] Social Media Authentication (Google, Facebook, ...)
- [ ] View profile, cập nhật thông tin cá nhân
- [ ] Change password
- [ ] Password recovery
- [ ] Quản lý nhiều địa chỉ giao hàng
- [ ] Product catalog theo category, có pagination ở mọi danh sách sản phẩm
- [ ] Product details kèm variants (inventory riêng cho từng variant)
- [ ] Search theo keyword
- [ ] Filter ít nhất 3 tiêu chí (bắt buộc brand và price min/max)
- [ ] Sort ít nhất 4 tiêu chí (name A-Z, Z-A, price tăng, giảm)
- [ ] Review (không cần login) và rating sao (cần login)
- [ ] Realtime review và rating với websocket
- [ ] Giỏ hàng: thêm, sửa số lượng, xoá, cập nhật realtime
- [ ] Cart summary: tổng tiền, thuế, phí ship
- [ ] Checkout nhiều bước, guest checkout tự tạo account
- [ ] Điền sẵn địa chỉ mặc định khi đã login, cho phép đổi địa chỉ
- [ ] Discount code 5 ký tự, tối đa 10 lần dùng, hiển thị hiệu lực trước khi thanh toán
- [ ] Màn hình order thành công và gửi email xác nhận
- [ ] Order tracking kèm lịch sử trạng thái (mới nhất ở trên)
- [ ] Order history và order details (login required)
- [ ] Loyalty points 10%, dùng được ngay ở order tiếp theo
- [ ] Format giá dễ đọc (e.g., 75,299,000đ)

## Admin Features

- [ ] Simple dashboard: tổng users, user mới, số orders, doanh thu, sản phẩm bán chạy (chart)
- [ ] Advanced dashboard: theo năm (mặc định), quý, tháng, tuần, khoảng ngày; có số order, doanh thu, lợi nhuận và chart so sánh
- [ ] Product management: thêm, sửa, xoá, categories, inventory
- [ ] User management: xem, cập nhật, ban user
- [ ] Order list: mới nhất ở trên, 20 items/trang, filter theo thời gian
- [ ] Order details và đổi trạng thái order
- [ ] Discount management: danh sách code, số lần dùng, các order đã áp dụng, tạo code mới

## Other Requirements

- [ ] UI/UX rõ ràng, dễ dùng
- [ ] Responsive trên mọi thiết bị
- [ ] Horizontal scaling: stateless, load balancing, có bằng chứng
- [ ] Commit đều đặn, chụp GitHub Insights
- [ ] Deploy: public hosting hoặc Docker Compose (mỗi component một container)

## Bonus (optional)

- [ ] CI/CD pipeline
- [ ] Microservices (ít nhất 3 services, giao tiếp qua RabbitMQ/Redis)
- [ ] AI features (chatbot, tìm bằng hình ảnh, sentiment analysis)
- [ ] ElasticSearch cho product search

## Submission

- [ ] Clean project, chuẩn bị thư mục `source`
- [ ] Quay `demo.mp4` (1080p, demo tất cả tính năng)
- [ ] Thư mục `git` với ảnh chụp GitHub Insights
- [ ] `Readme.txt`: hướng dẫn chạy, URL, username/password, bonus features
- [ ] Thư mục `Bonus` kèm bằng chứng
- [ ] Điền `Rubrik.docx`
- [ ] Nén thành `id1_fullname1_id2_fullname2.zip` và nộp trên elearning đúng hạn

# Overview

Xây dựng một website **E-commerce** hoàn chỉnh.

- Backend bắt buộc dùng Node.js framework (e.g., Express.js), ngôn ngữ **Javascript**
- Frontend được tự do chọn framework
- Có các tính năng cơ bản: user authentication, product management, order system

Website **chỉ được bán máy tính và linh kiện máy tính**. Bán điện thoại hoặc bất kì sản phẩm nào khác sẽ bị **0 điểm toàn bộ project**.

Những nội dung được đánh dấu màu tím trong đề phải làm đúng chính xác theo mô tả, không được thay đổi hay thêm bớt tính năng.

# Project Requirements

## 1. Landing Page (home page)

Trang đầu tiên user thấy khi vào website, phải hiển thị sản phẩm theo các mục:

- New Products
- Best Sellers
- Ít nhất 3 category khác (e.g., laptops, monitors, hard drives)

User không cần đăng nhập vẫn có thể xem và mua sản phẩm. Nếu mua khi chưa đăng nhập, hệ thống sẽ tự tạo account (nếu chưa có) và lưu lại order, sau này đăng nhập vào sẽ xem lại được các order cũ.

Nếu user mua sau khi đã đăng nhập, địa chỉ mặc định (nếu có) sẽ được điền sẵn ở phần checkout, user vẫn có thể đổi sang địa chỉ giao hàng khác.

Hệ thống chỉ cần 2 loại user: customer và một admin duy nhất.

## 2. User Management

- Registration và Login: khi tạo account user chỉ nhập email, full name và shipping address
- Social Media Authentication: đăng nhập bằng Google, Facebook, ...
- Profile Management: cập nhật thông tin cá nhân, đổi/khôi phục password, quản lý nhiều địa chỉ giao hàng

## 3. Product Management

- Product Catalog: một trang riêng (không phải landing page) hiển thị danh sách sản phẩm gồm name, price, image, short description (listview hoặc gridview)
  - Phân loại theo categories và tags để dễ điều hướng và tốt cho SEO
  - Pagination phải hoạt động **ở mọi nơi** có danh sách sản phẩm, luôn hiển thị số trang kể cả khi chỉ có 1 trang
  - Khi demo nếu không đủ data để thấy pagination thì sẽ bị xem như không có tính năng này
- Product Details: hiển thị name, price, brand, danh sách variants, short description **ít nhất 5 dòng**, **ít nhất 3 hình ảnh**
  - Bên dưới có phần comment và đánh giá sao
  - Mỗi variant có inventory riêng, để được full điểm mỗi sản phẩm phải có **ít nhất 2 variants**
- Product Ordering: sắp xếp sản phẩm theo **ít nhất 4 tiêu chí**, bắt buộc có name (A-Z, Z-A) và price (tăng dần, giảm dần)
- Search và Filtering: lọc theo **ít nhất 3 tiêu chí**, bắt buộc có brand và price (chọn được min và max)
- Reviews và Ratings:
  - Comment thì không cần đăng nhập
  - Rating sao thì phải đăng nhập (không cần đã mua hàng)
  - Nên dùng websocket để cập nhật comment và rating realtime không cần reload trang

## 4. Cart and Checkout

- Add to Cart: thêm, cập nhật số lượng, xoá sản phẩm, cập nhật realtime (số lượng, giá) không cần reload trang
- Cart Summary: tổng tiền, thuế, phí ship
- Checkout Process: nhiều bước để nhập thông tin thanh toán, giao hàng và xác nhận order
- Guest Checkout: mua hàng không cần tạo account
- Discount Codes:
  - Chuỗi **5 ký tự** chữ và số, do admin tạo
  - Không có ngày hết hạn, nhưng có giới hạn số lần dùng, **tối đa 10 lần** mỗi code
  - User phải thấy được code có hợp lệ không và được giảm bao nhiêu trước khi thanh toán

## 5. Order Management

- Order Creation: sau khi thanh toán thành công, tạo order gắn với account của user
  - Hiển thị màn hình thành công với đầy đủ thông tin order
  - Gửi email xác nhận chi tiết order
- Order Tracking: theo dõi trạng thái order (pending, confirmed, shipping, delivered)
  - Hiển thị lịch sử trạng thái dạng bảng kèm thời gian cập nhật, sắp xếp mới nhất ở trên cùng
- Order History: hiển thị mã order, ngày mua, tổng tiền, trạng thái, danh sách sản phẩm và số lượng
- Loyalty Programs: mỗi order được tích **10%** tổng tiền thành điểm
  - Ví dụ: order 1,000,000 VND → 100 điểm = 100,000 VND
  - Điểm dùng được ngay ở order tiếp theo, không có giới hạn gì thêm

## 6. Admin Management

- Dashboards:
  - Simple Dashboard: tổng số users, số user mới, số orders, doanh thu, sản phẩm bán chạy (dùng chart)
  - Advanced Dashboard: thống kê theo khoảng thời gian, mặc định theo năm, có thể đổi sang quý, tháng, tuần hoặc khoảng ngày tuỳ chọn
    - Mỗi khoảng thời gian phải có số order, doanh thu và lợi nhuận
    - Có chart so sánh doanh thu, lợi nhuận, số lượng sản phẩm và loại sản phẩm bán ra theo năm, tháng, quý, tuần
- Product Management: thêm, sửa, xoá sản phẩm, quản lý categories và inventory
- User Management: xem và quản lý users, ban hoặc cập nhật thông tin user
- Order Management: xem, cập nhật, xử lý order (e.g., đổi trạng thái từ pending sang confirmed)
- View order list: danh sách order toàn hệ thống, mới nhất ở trên, pagination khoảng **20 items/trang**
  - Filter theo: hôm nay, hôm qua, tuần này, tháng này, hoặc khoảng ngày (start - end)
- View order details: tên người mua, thời gian mua, tổng tiền, có dùng discount không, danh sách sản phẩm, có thể đổi trạng thái order
- Discount management: danh sách discount codes gồm thời gian tạo, giá trị giảm, số lần đã dùng / tối đa, danh sách order đã dùng code, và tạo code mới

**Không được thêm bất kì tính năng nào khác cho admin ngoài những tính năng trên.**

## 7. Deployment

Chọn 1 trong 2 cách. Làm được không có điểm cộng, nhưng không làm sẽ bị trừ 1.0 điểm (nếu tổng điểm >= 8.5) hoặc 0.5 điểm (nếu < 8.5).

### Public Hosting

- Deploy lên public cloud (e.g., Heroku, Vercel, AWS, Netlify)
- Cung cấp public URL
- Website phải hoạt động giống như ở local, nhớ cung cấp username/password của admin

### Docker Compose

- Mỗi component (frontend, backend, database, ...) nằm ở container riêng
- Cung cấp file `docker-compose.yml` kèm hướng dẫn chạy local
- Giảng viên phải chạy được project chỉ với lệnh `docker compose up -d`, các lệnh khác như `npm install` phải được cấu hình sẵn trong docker compose YAML file hoặc Dockerfile

## 8. Other Requirements

- UI/UX: giao diện rõ ràng, dễ dùng, điều hướng trực quan, load nhanh
- Team Collaboration: dùng Git, chụp màn hình GitHub Insights làm bằng chứng
  - Project phải kéo dài **ít nhất 1 tháng** tính từ ngày bắt đầu
  - Mỗi thành viên **ít nhất 2 commits/tuần**
  - Nhóm 1 người không có điểm teamwork
- Responsive Design: hiển thị tốt trên mọi thiết bị (Bootstrap, CSS Grid, ...)
- Horizontal Scaling: stateless architecture, load balancing, có thể cân nhắc microservices, phải có bằng chứng rõ ràng

## 9. Bonus Features

Mỗi tính năng hoàn chỉnh được cộng 0.5 điểm, tối đa 2 điểm:

- CI/CD pipeline: Jenkins, Github Actions, Circle CI, GitLab CI/CD, hoặc giải pháp của top 3 Cloud provider
- Microservices Architecture: ngoài frontend và database phải có **ít nhất 3 services** khác, có giao tiếp bất đồng bộ qua RabbitMQ hoặc Redis
- AI features: chatbot gợi ý sản phẩm, tìm sản phẩm bằng hình ảnh, Sentiment Analysis cho reviews
- ElasticSearch cho Product Search

Các bonus feature đã làm phải được ghi rõ trong self-evaluation form, README, video demo kèm bằng chứng cụ thể.

# Rubrik

## Customer Features - 6.0 points

Mỗi tính năng 0.25 điểm:

- Social Media Authentication
- View profile page
- Change password
- Password recovery
- Manage multiple delivery address
- View purchase history (login required)
- View purchase details (login required)
- Landing Page
- Product Catalog (view products by category)
- Pagination
- View product details
- View product variants (trong cùng trang detail)
- Product search by keyword
- Product filtering
- Product ordering (e.g., by price, time)
- Display shopping cart
- Update shopping cart
- Checkout process
- Using discount code when making purchase
- Email notification (sau khi đặt order)
- Product review (comment)
- Product rating with stars
- Realtime update review và rating với websocket
- Loyalty Programs

## Admin Features - 2.0 points

- User Management - 0.25
- Product Management - 0.25
- Discount management - 0.25
- View order list - 0.25
- View order details (và đổi trạng thái order) - 0.25
- Simple Dashboard - 0.25
- Advanced Dashboard - **0.5**

## Other Requirements - 2.0 points

- UI/UX - **0.5** (chỉ có điểm nếu trên mức trung bình, giao diện cơ bản không có điểm)
- Teamworking - **0.5** (làm một mình hoặc không có GitHub Insights thì không có điểm)
- Responsive - **0.5** (chỉ có điểm nếu trên mức trung bình)
- Horizontal scaling - **0.5**

## Mức đánh giá

- 0 điểm: không có, không hoạt động, hoặc lỗi nghiêm trọng không dùng được
- 1/2 điểm: có nhưng chưa hoàn chỉnh, validate input kém, có lỗ hổng bảo mật, không theo chuẩn
- Full điểm: hoàn chỉnh, bảo mật, đúng chuẩn, không có lỗi lớn

## Avoid these

Hiển thị giá lấy thẳng từ database như "75299000", khó đọc. Nên format thành "75,299,000đ" có dấu phẩy và đơn vị tiền tệ.

Danh sách order chỉ "select all" từ database, sắp xếp tăng dần làm order mới nằm dưới cùng, không có pagination, thông tin quan trọng (tổng tiền, tên người mua, trạng thái, ngày) hiển thị không rõ ràng. Nên sắp xếp giảm dần theo ngày, có pagination, format dữ liệu rõ ràng và dùng màu sắc phù hợp.

# Submitions

## Source Code

Thư mục `source`

- Không dùng docker compose: toàn bộ source code (frontend, backend) và file database liên quan, chạy được trên máy giảng viên, phải clean bớt file không cần thiết
- Dùng docker compose: toàn bộ source code các module, file docker-compose và hướng dẫn chạy trên máy giảng viên

## Video Presentation

File `demo.mp4`

- Một thành viên quay màn hình demo **TẤT CẢ** tính năng theo self-assessment
- Độ phân giải tối thiểu 1080p, âm thanh rõ ràng, không giải thích lý thuyết

## Git

Thư mục `git`

- Ảnh chụp màn hình thể hiện làm việc nhóm trên GitHub/GitLab
- Thời gian project ít nhất 1 tháng, mỗi thành viên ít nhất 2 commits/tuần

## Readme.txt

- Hướng dẫn build và chạy project
- URL + thông tin đăng nhập server (nếu có)
- Username/password của các account có sẵn data để chấm
- Ghi rõ các bonus feature đã làm

## Bonus

Thư mục `Bonus`

- Mô tả các tính năng bonus kèm bằng chứng, trình bày rõ ràng, ngắn gọn, thuyết phục

## Rubrik.docx

- Tự đánh giá mức độ hoàn thành các tính năng, giảng viên sẽ cung cấp file khi nộp bài
- Ghi public URL và username/password đăng nhập

## Cách nộp

- Tất cả để trong thư mục `id1_fullname1_id2_fullname2`, nén thành file ZIP cùng tên (e.g., `id1_fullname1_id2_fullname2.zip`)
- Một thành viên đại diện nộp trên hệ thống elearning, không nhận qua email

# Important Notes

- Project phải dùng **Nodejs** và ngôn ngữ **Javascript**, được dùng bất kì library/framework nào dựa trên Node.js
- Nộp project không liên quan (e.g., dùng source của e-commerce khác và chỉ làm vài tính năng) sẽ bị 0 điểm
- Essay và Final Project là độc lập, tất cả thành viên phải tham gia cả hai. Essay do giảng viên thực hành chấm, Final Project do giảng viên lý thuyết chấm
- Không được chia sẻ code giữa các nhóm hay lấy code trên internet, code giống nhau (kể cả một phần) sẽ bị 0 điểm cả nhóm
- Không nộp source code: 0 điểm cả nhóm
- Không nộp file `rubrik.docx`: không được chấm
- Không deploy (public hosting hoặc Docker Compose) hoặc không có video demo: không được chấm

## Các trường hợp bị trừ điểm

- Nộp trễ: trễ 1 ngày trừ 1 điểm (trễ từ 1 giây đến dưới 1 ngày tính là 1 ngày)
- Cấu hình project phức tạp mà không có hướng dẫn cụ thể để giảng viên chạy: trừ 2 điểm
- Không clean project trước khi nộp: trừ 0.5 điểm
- Thiếu thông tin chấm bài (thiếu username/password, đặt tên file sai, thiếu nội dung yêu cầu): trừ 1.0 điểm
