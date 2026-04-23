<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Vocabulary & Grammar Test - 45 Questions</title>
  <style>
    :root{--bg:#f6f8fb;--card:#fff;--accent:#2b6cb0;--correct:#28a745;--wrong:#dc3545}
    body{font-family:system-ui,-apple-system,Segoe UI,Roboto,'Helvetica Neue',Arial;margin:0;background:var(--bg);color:#111}
    header{background:linear-gradient(90deg,#1f6fb8,#2b6cb0);color:white;padding:18px 24px}
    .container{max-width:980px;margin:18px auto;padding:18px}
    .card{background:var(--card);border-radius:10px;box-shadow:0 6px 20px rgba(20,20,40,0.06);padding:18px}
    h1{margin:0 0 6px;font-size:20px}
    p.lead{margin:6px 0 16px;color:#334155}
    .question{padding:12px;border-radius:8px;margin-bottom:10px;border:1px solid #eef2f7}
    .qnum{font-weight:600;margin-bottom:6px}
    .options{display:flex;gap:12px;flex-wrap:wrap}
    label.opt{flex:1;min-width:150px;background:#f8fafc;padding:10px;border-radius:8px;border:1px solid #e6eef8;cursor:pointer}
    input[type=radio]{margin-right:8px}
    .controls{display:flex;gap:10px;align-items:center;margin-top:14px}
    button{background:var(--accent);color:white;border:none;padding:10px 14px;border-radius:8px;cursor:pointer}
    button.secondary{background:#6b7280}
    .result{margin-top:14px;padding:12px;border-radius:8px}
    .correct{background:rgba(40,167,69,0.08);border:1px solid rgba(40,167,69,0.18);color:var(--correct)}
    .wrong{background:rgba(220,53,69,0.06);border:1px solid rgba(220,53,69,0.12);color:var(--wrong)}
    .small{font-size:13px;color:#475569}
    footer{max-width:980px;margin:20px auto;text-align:center;color:#64748b}
    @media (max-width:700px){.options{flex-direction:column}}
  </style>
</head>
<body>
  <header>
    <div class="container">
      <h1>Vocabulary & Grammar - 45-question Test</h1>
      <div class="small">Điền chọn A, B, C hoặc D cho mỗi câu. Nhấn "Nộp bài" để chấm điểm và xem đáp án.</div>
    </div>
  </header>

  <main class="container">
    <div class="card">
      <form id="quizForm">
        <div id="questions"></div>

        <div class="controls">
          <button type="button" id="submitBtn">Nộp bài</button>
          <button type="button" id="resetBtn" class="secondary">Làm lại</button>
          <div id="score" style="margin-left:auto"></div>
        </div>
      </form>

      <div id="feedback" style="margin-top:12px"></div>
    </div>
  </main>

  <footer>
    <div class="small">Đề gốc: Bài trắc nghiệm 50 câu (Vocabulary & Grammar)</div>
  </footer>

  <script>
  // --- QUESTIONS DATA ---
    const questionsData = [
  {
    id: 1,
    q: "Nhóm nghề sửa chữa và bảo trì máy tính chủ yếu liên quan đến lĩnh vực nào?",
    opts: {
      A: "Lắp ráp, chẩn đoán và khắc phục sự cố phần cứng, phần mềm.",
      B: "Thiết kế đồ họa và lập trình phần mềm.",
      C: "Quản lý doanh nghiệp và tài chính.",
      D: "Lắp đặt hệ thống điện dân dụng."
    },
    answer: "A"
  },
  {
    id: 2,
    q: "Công việc nào sau đây là của người làm nghề sửa chữa và bảo trì máy tính?",
    opts: {
      A: "Xác định và khắc phục lỗi phần cứng làm cho máy tính ngừng hoạt động.",
      B: "Khắc phục những lỗ hổng về an toàn thông tin.",
      C: "Quản lí, vận hành các thiết bị mạng.",
      D: "Phân tích và xác định nhu cầu của hệ thống thông tin."
    },
    answer: "A"
  },
  {
    id: 3,
    q: "Mục đích chính của dịch vụ sửa chữa và bảo trì máy tính là gì?",
    opts: {
      A: "Làm cho máy tính chạy nhanh hơn bình thường",
      B: "Duy trì sự ổn định của máy tính và thiết bị liên quan",
      C: "Chỉ để nâng cấp phần mềm",
      D: "Chỉ thay thế linh kiện khi hỏng"
    },
    answer: "B"
  },
  {
    id: 4,
    q: "Công việc nào KHÔNG liên quan đến phần cứng?",
    opts: {
      A: "Kiểm soát và duy trì hoạt động của máy tính",
      B: "Đảm bảo kết nối máy tính vào mạng",
      C: "Lắp đặt, sửa chữa linh kiện",
      D: "Khắc phục lỗi phần cứng"
    },
    answer: "B"
  },
  {
    id: 5,
    q: "Công việc nào KHÔNG liên quan đến phần mềm?",
    opts: {
      A: "Cài đặt driver thiết bị",
      B: "Đảm bảo kết nối mạng",
      C: "Cập nhật phần mềm",
      D: "Phát hiện nguyên nhân hỏng thiết bị"
    },
    answer: "D"
  },
  {
    id: 6,
    q: "Việc cập nhật công nghệ mới là kĩ năng gì?",
    opts: {
      A: "Kĩ năng học hỏi, cập nhật kiến thức",
      B: "Kĩ năng giải quyết vấn đề",
      C: "Kĩ năng giao tiếp",
      D: "Kĩ năng quản lí thời gian"
    },
    answer: "A"
  },
  {
    id: 7,
    q: "Nguyên lí hoạt động của máy tính được đào tạo nhiều ở bậc học nào?",
    opts: {
      A: "Cao học",
      B: "Đại học",
      C: "Cao đẳng",
      D: "Trung cấp nghề"
    },
    answer: "B"
  },
  {
    id: 8,
    q: "Phương án SAI về kiến thức của kỹ sư an toàn thông tin là gì?",
    opts: {
      A: "Hệ điều hành, mạng",
      B: "Thiết kế mạng",
      C: "Mã hóa thông tin",
      D: "Công cụ xâm nhập"
    },
    answer: "B"
  },
  {
    id: 9,
    q: "Phương án SAI về nhiệm vụ của kỹ sư quản trị mạng là gì?",
    opts: {
      A: "Quản lý thiết bị mạng",
      B: "Bảo vệ mạng",
      C: "Lập trình CSDL",
      D: "Khắc phục sự cố mạng"
    },
    answer: "C"
  },
  {
    id: 10,
    q: "Nghề nào chịu trách nhiệm thiết kế cấu trúc dữ liệu?",
    opts: {
      A: "Quản trị mạng",
      B: "Front-end",
      C: "Chuyên gia CSDL",
      D: "Kiểm thử phần mềm"
    },
    answer: "C"
  },
  {
    id: 11,
    q: "Trong dự án phần mềm giáo dục, cần làm gì để phần mềm hoàn thiện hơn?",
    opts: {
      A: "Không cần phản hồi người dùng",
      B: "Làm theo chỉ đạo",
      C: "Dựa vào kinh nghiệm cá nhân",
      D: "Dựa vào phản hồi người dùng và cập nhật liên tục"
    },
    answer: "D"
  },
  {
    id: 12,
    q: "Nhóm nghề quản trị CNTT KHÔNG liên quan đến công việc nào?",
    opts: {
      A: "Quản trị mạng",
      B: "Bảo mật hệ thống",
      C: "Quản trị hệ thống",
      D: "Phát triển phần mềm"
    },
    answer: "D"
  },
  {
    id: 13,
    q: "Vai trò của quản trị hệ thống mạng là gì?",
    opts: {
      A: "Cài phần mềm văn phòng",
      B: "Đảm bảo mạng ổn định và an toàn",
      C: "Viết bài quảng cáo",
      D: "Sửa máy in"
    },
    answer: "B"
  },
  {
    id: 14,
    q: "Việc nào KHÔNG thuộc nhóm quản trị CNTT?",
    opts: {
      A: "Quản trị mạng",
      B: "Quản trị CSDL",
      C: "Phát triển game",
      D: "An toàn thông tin"
    },
    answer: "C"
  },
  {
    id: 15,
    q: "Kỹ năng quan trọng của quản trị viên mạng là gì?",
    opts: {
      A: "Chỉ biết dùng máy tính",
      B: "Hiểu mạng, bảo mật, xử lý sự cố",
      C: "Chỉ cần giao tiếp",
      D: "Thiết kế đồ họa"
    },
    answer: "B"
  },
  {
    id: 16,
    q: "Thách thức của quản trị an toàn thông tin là gì?",
    opts: {
      A: "Cập nhật mối đe dọa và bảo vệ dữ liệu",
      B: "Lập trình web",
      C: "Kiểm tra tốc độ mạng",
      D: "Viết hướng dẫn"
    },
    answer: "A"
  },
  {
    id: 17,
    q: "Ngành học phù hợp để làm quản trị CSDL là gì?",
    opts: {
      A: "CNTT định hướng quản trị hệ thống",
      B: "Tâm lý học",
      C: "Truyền thông",
      D: "Ngôn ngữ học"
    },
    answer: "A"
  },
  {
    id: 18,
    q: "Cách chọn ngành phù hợp là gì?",
    opts: {
      A: "Đánh giá năng lực, thị trường, điểm chuẩn",
      B: "Theo bạn bè",
      C: "Chọn điểm thấp",
      D: "Theo xu hướng"
    },
    answer: "A"
  },
  {
    id: 19,
    q: "Bạn thích CNTT và đồ họa nên chọn ngành gì?",
    opts: {
      A: "Thiết kế đồ họa",
      B: "Kiểm thử",
      C: "Quản trị mạng",
      D: "An toàn thông tin"
    },
    answer: "A"
  },
  {
    id: 20,
    q: "Mục đích của hội thảo hướng nghiệp là gì?",
    opts: {
      A: "Chọn trường đại học",
      B: "Định hướng nghề và cung cấp thông tin",
      C: "Giới thiệu phần mềm",
      D: "Dạy lập trình"
    },
    answer: "B"
  },
  {    
    id: 21,
    q: "Hội thảo hướng nghiệp có thể tổ chức dưới hình thức nào?",
    opts: {
      A: "Trực tiếp tại trường",
      B: "Trực tuyến",
      C: "Cả trực tiếp và trực tuyến",
      D: "Chỉ tài liệu in"
    },
    answer: "C"
  },
  {
    id: 22,
    q: "Ngành nào thuộc lĩnh vực CNTT?",
    opts: {
      A: "Kỹ sư xây dựng",
      B: "Bác sĩ",
      C: "Phát triển phần mềm",
      D: "Luật sư"
    },
    answer: "C"
  },
  {
    id: 23,
    q: "Xu hướng ngành CNTT trong tương lai?",
    opts: {
      A: "Giảm nhu cầu",
      B: "Ổn định",
      C: "Tăng mạnh do số hóa và AI",
      D: "Chỉ phát triển ở nước lớn"
    },
    answer: "C"
  },
  {
    id: 24,
    q: "Yếu tố giúp chọn nghề phù hợp?",
    opts: {
      A: "Đánh giá khả năng và sở thích",
      B: "Theo bạn bè",
      C: "Theo phim",
      D: "Ngẫu nhiên"
    },
    answer: "A"
  },
  {
    id: 25,
    q: "Vì sao Machine Learning và NLP quan trọng?",
    opts: {
      A: "Tạo phần cứng mạnh",
      B: "Giúp máy tự học và hiểu ngôn ngữ",
      C: "Chỉ xử lí ảnh",
      D: "Không cần dữ liệu"
    },
    answer: "B"
  },
  {
    id: 26,
    q: "Đặc trưng của học máy là gì?",
    opts: {
      A: "Dựa vào quy tắc lập trình",
      B: "Học từ dữ liệu và dự đoán",
      C: "Thay đổi dữ liệu đầu vào",
      D: "Tự tạo chương trình mới"
    },
    answer: "B"
  },
  {
    id: 27,
    q: "Phương pháp dùng dữ liệu có nhãn?",
    opts: {
      A: "Học có giám sát",
      B: "Không giám sát",
      C: "Học sâu",
      D: "Tăng cường"
    },
    answer: "A"
  },
  {
    id: 28,
    q: "Dữ liệu có nhãn là gì?",
    opts: {
      A: "Không có chỉ dẫn",
      B: "Có nhãn cụ thể",
      C: "Không cấu trúc",
      D: "Chỉ phân nhóm"
    },
    answer: "B"
  },
  {
    id: 29,
    q: "Chia train/test để làm gì?",
    opts: {
      A: "Giảm dữ liệu",
      B: "Kiểm tra mô hình với dữ liệu mới",
      C: "Tránh trùng lặp",
      D: "Giảm thời gian"
    },
    answer: "B"
  },
  {
    id: 30,
    q: "Phân loại email spam thuộc loại nào?",
    opts: {
      A: "Không giám sát",
      B: "Có giám sát",
      C: "Học sâu",
      D: "Tăng cường"
    },
    answer: "B"
  },
  {
    id: 31,
    q: "Vì sao học máy nhận dạng giọng nói?",
    opts: {
      A: "Lập trình rõ đặc điểm",
      B: "Học từ dữ liệu",
      C: "Thay đổi dữ liệu",
      D: "Không cần dữ liệu"
    },
    answer: "B"
  },
  {
    id: 32,
    q: "Quy trình học máy gồm gì?",
    opts: {
      A: "Thu thập → xử lý → huấn luyện → đánh giá → sử dụng",
      B: "Thu thập → phân tích → dùng",
      C: "Chọn thuật toán → phân tích",
      D: "Thu thập → triển khai"
    },
    answer: "A"
  },
  {
    id: 33,
    q: "Mô hình chẩn đoán bệnh học từ đâu?",
    opts: {
      A: "Triệu chứng và xét nghiệm",
      B: "Từ bác sĩ",
      C: "Từ bản đồ",
      D: "Từ điều trị"
    },
    answer: "A"
  },
  {
    id: 34,
    q: "Dữ liệu ảnh đa dạng thì làm gì?",
    opts: {
      A: "Lập trình rõ đặc điểm",
      B: "Cung cấp nhiều ảnh để học",
      C: "Ít ảnh",
      D: "Không nhãn"
    },
    answer: "B"
  },
  {
    id: 35,
    q: "Phát hiện gian lận dùng phương pháp nào?",
    opts: {
      A: "Có giám sát",
      B: "Không giám sát",
      C: "Học sâu",
      D: "Tăng cường"
    },
    answer: "A"
  },
  {
    id: 36,
    q: "Khoa học dữ liệu là gì?",
    opts: {
      A: "Phân tích dữ liệu tìm tri thức",
      B: "Quản lý phần mềm",
      C: "Không cần dữ liệu",
      D: "Chỉ dữ liệu lớn"
    },
    answer: "A"
  },
  {
    id: 37,
    q: "Mục tiêu chính của khoa học dữ liệu?",
    opts: {
      A: "Thu thập dữ liệu",
      B: "Phân tích để ra quyết định",
      C: "Lưu trữ",
      D: "Phân phối"
    },
    answer: "B"
  },
  {
    id: 38,
    q: "Công cụ của khoa học dữ liệu?",
    opts: {
      A: "Toán, thống kê, CNTT",
      B: "Công cụ tìm kiếm",
      C: "Soạn thảo",
      D: "CSDL"
    },
    answer: "A"
  },
  {
    id: 39,
    q: "Phân loại khách hàng dùng gì?",
    opts: {
      A: "Có giám sát",
      B: "Không giám sát",
      C: "Học sâu",
      D: "Hồi quy"
    },
    answer: "B"
  },
  {
    id: 40,
    q: "Tối ưu sản xuất cần gì?",
    opts: {
      A: "Quản lý tài nguyên",
      B: "Dùng ML phân tích",
      C: "Dự đoán số lượng",
      D: "Giả thuyết"
    },
    answer: "B"
  },
  {
    id: 41,
    q: "Mô phỏng là gì?",
    opts: {
      A: "Tạo sản phẩm mới",
      B: "Sao chép hoàn toàn",
      C: "Mô hình ảo tái hiện hệ thống",
      D: "Chỉ dùng quân sự"
    },
    answer: "C"
  },
  {
    id: 42,
    q: "Lợi ích mô phỏng?",
    opts: {
      A: "Mô tả động vật",
      B: "Thay thế hoàn toàn",
      C: "Luyện tập an toàn",
      D: "Bỏ huấn luyện"
    },
    answer: "C"
  },
  {
    id: 43,
    q: "Mô phỏng trong kỹ thuật giúp gì?",
    opts: {
      A: "Không cần kiểm tra",
      B: "Phát hiện lỗi trước sản xuất",
      C: "Giảm sáng tạo",
      D: "Giảm chính xác"
    },
    answer: "B"
  },
  {
    id: 44,
    q: "Tùy chỉnh mô phỏng giúp gì?",
    opts: {
      A: "Tăng phức tạp",
      B: "Không cần chuyên gia",
      C: "Tìm lỗi phần mềm",
      D: "Kiểm tra giả thuyết"
    },
    answer: "D"
  },
  {
    id: 45,
    q: "Dạy hệ Mặt Trời bằng mô phỏng?",
    opts: {
      A: "Tưởng tượng",
      B: "Xem phim",
      C: "Phần mềm 3D tương tác",
      D: "Tranh tĩnh"
    },
    answer: "C"
  },
  {
    id: 46,
    q: "Mô phỏng trong game?",
    opts: {
      A: "Ảnh ngẫu nhiên",
      B: "Mô hình hành vi thực",
      C: "Ảnh đơn giản",
      D: "Chỉ âm thanh"
    },
    answer: "B"
  },
  {
    id: 47,
    q: "Lĩnh vực ít dùng mô phỏng?",
    opts: {
      A: "Y học",
      B: "Giải trí",
      C: "Tài chính kế toán",
      D: "Giáo dục"
    },
    answer: "C"
  },
  {
    id: 48,
    q: "Vai trò phần mềm mô phỏng?",
    opts: {
      A: "Chỉ hình ảnh",
      B: "Tạo mô hình ảo tương tác",
      C: "Chỉ quân sự",
      D: "Thay thế hoàn toàn"
    },
    answer: "B"
  },
  {
    id: 49,
    q: "Lợi ích mô phỏng trong giáo dục?",
    opts: {
      A: "Thay giáo viên",
      B: "Tăng độ khó",
      C: "Thực hành an toàn",
      D: "Phụ thuộc máy"
    },
    answer: "C"
  },
  {
    id: 50,
    q: "Vì sao dùng mô phỏng thay thực tế?",
    opts: {
      A: "Đẹp hơn",
      B: "Chính xác hơn",
      C: "Dễ hơn",
      D: "Tiết kiệm và an toàn"
    },
    answer: "D"
  },
  {
    id: 51,
    q: "Dữ liệu lớn có đặc điểm gì quan trọng?",
    opts: {
      A: "Có thể được xử lý dễ dàng và nhanh chóng.",
      B: "Không có kích thước lớn và dễ phân tích.",
      C: "Có sự đa dạng về các loại dữ liệu và thường xuyên được cập nhật.",
      D: "Không thay đổi theo thời gian."
    },
    answer: "C"
  },
  {
    id: 52,
    q: "Khi ứng dụng Khoa học dữ liệu để phân tích hành vi của khách hàng, bạn sẽ sử dụng kỹ thuật nào để phân loại khách hàng thành các nhóm?",
    opts: {
      A: "Học có giám sát",
      B: "Học không giám sát",
      C: "Học sâu",
      D: "Học máy hồi quy"
    },
    answer: "B"
  },
  {
    id: 53,
    q: "Máy tính đóng vai trò quan trọng trong tất cả các giai đoạn của quy trình khoa học dữ liệu như thu thập, xử lí, phân tích và trực quan hóa dữ liệu. Phương án nào sau đây không phải là vai trò của máy tính trong khoa học dữ liệu?",
    opts: {
      A: "Hạn chế khả năng lưu trữ dữ liệu lớn",
      B: "Phân tích và khai phá dữ liệu phức tạp",
      C: "Tạo ra các biểu diễn trực quan của dữ liệu",
      D: "Tự động hoá các nhiệm vụ lặp lại trong xử lí dữ liệu"
    },
    answer: "A"
  },
  {
    id: 54,
    q: "Dự án Hệ gene người đã ứng dụng sức mạnh máy tính để giải mã chuỗi gene phức tạp của con người, giúp hoàn thành khối lượng công việc khổng lồ trong thời gian ngắn. Câu trả lời nào sau đây là kết quả trực tiếp của việc sử dụng máy tính trong Dự án Hệ gene người?",
    opts: {
      A: "Tạo ra các mẫu sinh học nhân tạo",
      B: "Hoàn thành bản đồ gene trong thời gian ngắn hơn",
      C: "Giảm độ dài hệ gene người",
      D: "Tạo ra thiết bị xét nghiệm cầm tay"
    },
    answer: "B"
  },
  {
    id: 55,
    q: "Trong khoa học dữ liệu, trực quan hóa dữ liệu giúp trình bày kết quả phân tích một cách dễ hiểu và sinh động. Phương án nào sau đây giải thích đúng nhất vai trò của trực quan hoá dữ liệu?",
    opts: {
      A: "Chuyển đổi dữ liệu thành file văn bản để lưu trữ",
      B: "Giúp giảm độ phức tạp của mô hình dữ liệu bằng cách loại bỏ thuộc tính",
      C: "Hỗ trợ khám phá, trình bày kết quả và giao tiếp hiệu quả với người dùng",
      D: "Là bước cuối cùng để mã hóa dữ liệu trước khi xử lí"
    },
    answer: "C"
  },
  {
    id: 56,
    q: "Khi phân tích dữ liệu gene, các máy tính sử dụng khả năng xử lí song song để tăng tốc độ tính toán. Cách nào sau đây giúp quá trình phân tích dữ liệu gene diễn ra nhanh hơn nhờ máy tính?",
    opts: {
      A: "Sử dụng phần mềm vẽ biểu đồ thủ công",
      B: "Xử lí dữ liệu theo từng đoạn, một cách tuần tự",
      C: "Tăng bộ nhớ RAM mà không cần thêm lõi xử lí",
      D: "Chia nhỏ và xử lí đồng thời nhiều phần của dữ liệu bằng tính toán song song"
    },
    answer: "D"
  },
  {
    id: 57,
    q: "Bạn được giao một nhiệm vụ phân tích dữ liệu lớn với yêu cầu tự động hoá, giảm lỗi thao tác tay, và cần tốc độ xử lí nhanh. Cách nào sau đây là phù hợp nhất để thực hiện nhiệm vụ này?",
    opts: {
      A: "Sử dụng phần mềm bảng tính và nhập liệu thủ công",
      B: "Áp dụng thuật toán học máy trên nền tảng điện toán đám mây có hỗ trợ tự động hoá",
      C: "Sử dụng điện thoại để xử lí dữ liệu qua ứng dụng di động",
      D: "Chia sẻ dữ liệu cho từng người trong nhóm để xử lí riêng"
    },
    answer: "B"
  },
  {
    id: 58,
    q: "Một nhóm nghiên cứu quốc tế cùng hợp tác giải mã hệ gene người, trong đó dữ liệu được thu thập ở nhiều nơi và xử lí tập trung. Phương án nào sau đây thể hiện đúng nhất lợi ích của việc dùng máy tính trong bối cảnh này?",
    opts: {
      A: "Cho phép người dùng sao chép dữ liệu thủ công giữa các quốc gia",
      B: "Tăng thời gian phản hồi khi có nhiều dữ liệu cùng lúc",
      C: "Tích hợp dữ liệu từ các nhóm nghiên cứu để phân tích thống nhất và hiệu quả hơn",
      D: "Giảm sự hợp tác khoa học do phụ thuộc vào máy tính"
    },
    answer: "C"
  }];
  function shuffleArray(array) {
    for (let i = array.length - 1; i > 0; i--) {
      const j = Math.floor(Math.random() * (i + 1));
      [array[i], array[j]] = [array[j], array[i]];
    }
  }
shuffleArray(questionsData);

const container = document.getElementById('questions');

questionsData.forEach((item, index) => {
  const qNumber = index + 1;

  const div = document.createElement('div');
  div.className = 'question';
  div.id = 'q' + qNumber;

  div.innerHTML = `
    <div class="qnum">Câu ${qNumber}:</div>
    <div class="qtext">${item.q}</div>
    <div class="options">
      ${Object.entries(item.opts).map(([key, val]) => `
        <label class="opt">
          <input type="radio" name="q${qNumber}" value="${key}">
          <strong>${key}.</strong> ${val}
        </label>
      `).join('')}
    </div>
  `;

  container.appendChild(div);
});


  // grading logic
  const submitBtn = document.getElementById('submitBtn');
  const resetBtn = document.getElementById('resetBtn');
  const scoreDiv = document.getElementById('score');
  const feedbackDiv = document.getElementById('feedback');

  submitBtn.addEventListener('click', ()=>{
  let correctCount = 0;
  let total = questionsData.length;

  for(let i=0;i<total;i++){
    const qNumber = i + 1;
    const selected = document.querySelector(`input[name="q${qNumber}"]:checked`);
    const qDiv = document.getElementById('q'+qNumber);

    qDiv.classList.remove('correct','wrong');
    const old = qDiv.querySelector('.note'); if(old) old.remove();

    const note = document.createElement('div');
    note.className = 'note small';

    if(!selected){
      note.textContent = '(Chưa trả lời)';
      qDiv.appendChild(note);
      continue;
    }

    if(selected.value === questionsData[i].answer){
      correctCount++;
      qDiv.classList.add('correct');
      note.textContent = `Đúng — đáp án: ${questionsData[i].answer}`;
    } else {
      qDiv.classList.add('wrong');
      note.textContent = `Sai — đáp án đúng: ${questionsData[i].answer}`;
    }

    qDiv.appendChild(note);
  }

  scoreDiv.innerHTML = `<strong>Kết quả: ${correctCount}/${total}</strong>`;
  submitBtn.disabled = true;
});

  resetBtn.addEventListener('click', ()=>{
    document.getElementById('quizForm').reset();
    // clear highlights/notes
    for(let i=1;i<=questionsData.length;i++){
      const qDiv = document.getElementById('q'+i);
      qDiv.classList.remove('correct','wrong');
      const note = qDiv.querySelector('.note'); if(note) note.remove();
      const un = qDiv.querySelector('.small'); if(un) un.remove();
    }
    scoreDiv.innerHTML='';
    feedbackDiv.innerHTML='';
    submitBtn.disabled = false;
  });
  </script>
</body>
</html>
