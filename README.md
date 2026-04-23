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
  { id: 1, q: "Nhóm nghề sửa chữa và bảo trì máy tính chủ yếu liên quan đến lĩnh vực nào?", opts: { A: "Lắp ráp, chẩn đoán và khắc phục sự cố phần cứng, phần mềm.", B: "Thiết kế đồ họa và lập trình phần mềm.", C: "Quản lý doanh nghiệp và tài chính.", D: "Lắp đặt hệ thống điện dân dụng." }, answer: "A" },
  { id: 2, q: "Công việc nào sau đây là của người làm nghề Sửa chữa và bảo trì máy tính?", opts: { A: "Xác định và khắc phục lồi phần cứng làm cho máy tính của khách hàng ngừng hoạt động.", B: "Khắc phục những lỗ hổng về an toàn thông tin.", C: "Quản lí, vận hành các thiết bị mạng.", D: "Phân tích và xác định nhu cầu của hệ thống thông tin, từ đó thiết lập chính sách và quy trình với người dùng trong hệ thống." }, answer: "A" },
  { id: 3, q: "Đâu là mục đích chính của dịch vụ sửa chữa và bảo trì máy tính trong các phương án sau:", opts: { A: "Làm cho máy tính chạy nhanh hơn bình thường", B: "Duy trì sự ổn định của máy tính cũng như các thiết bị có liên quan tới máy tính", C: "Chỉ để nâng cấp phần mềm trên máy tính", D: "Chỉ thay thế linh kiện phần cứng khi hỏng hóc" }, answer: "B" },
  { id: 4, q: "Với người làm nghề sửa chữa và bảo trì máy tính thì những việc nào sau đâu KHÔNG liên quan đến phần cứng:", opts: { A: "Kiểm soát và duy trì hoạt động của máy tính", B: "Đảm bảo kết nối máy tính vào mạng", C: "Lắp đặt, sửa chữa hoặc thay thế các linh kiện máy tính bị hỏng", D: "Xác định và khắc phục lỗi phần cứng khi có sự cố xảy ra" }, answer: "B" },
  { id: 5, q: "Với người làm nghề sửa chữa và bảo trì máy tính thì những việc nào sau đâu KHÔNG liên quan đến phần mềm:", opts: { A: "Cài đặt hoặc cập nhật phần điều khiển thiết bị ngoại vi", B: "Đảm bảo kết nối máy tính vào mạng", C: "Cập nhật các phiên bản mới của phần mềm để đảm bảo tính an toàn và hiệu quả", D: "Phát hiện nguyên nhân hỏng thiết bị để biết liệu có thể sửa, thay thế hay cấu hình lại" }, answer: "D" },
  { id: 6, q: "Với người làm nghề sửa chữa và bảo trì máy tính thì việc theo dõi, cập nhật để có hiểu biết về công nghệ mới là kĩ năng nào trong các kĩ năng sau:", opts: { A: "Kĩ năng học hỏi, cập nhật kiến thức", B: "Kĩ năng giải quyết vấn đề", C: "Kĩ năng giao tiếp", D: "Kĩ năng quản lí thười gian" }, answer: "A" },
  { id: 7, q: "Nguyên lí hoạt động của máy tính và thiết bị công nghệ thông tin được đào tạo nhiều ở bậc học nào sau đây:", opts: { A: "Cao học", B: "Đại học", C: "Cao đẳng", D: "Trung cấp nghề" }, answer: "B" },
  { id: 8, q: "Hãy chọn phương án SAI về những kiến thức mà kỹ sư An toàn thông tin cần có?", opts: { A: "Hệ điều hành; hệ thống mạng và một số giao thức mạng.", B: "Thiết kế mạng", C: "Bảo mật thông tin, mã hóa thông tin.", D: "Tường lửa, các công cụ xâm nhập." }, answer: "B" },
  { id: 9, q: "Hãy chọn phương án SAI về nhiệm vụ của Kỹ sư quản trị mạng?", opts: { A: "Quản lý các thiết bị mạng, vận hành mạng, thiết lập mạng theo yêu cầu công việc, cấu hình và điều chỉnh hiệu năng mạng.", B: "Bảo vệ mạng trước những nguy cơ: bị tấn công, truy cập mạng bất hợp pháp.", C: "Lập trình các chương trình về quản lý CSDL của người dùng mạng.", D: "Khắc phục sự cố mạng." }, answer: "C" },
  { id: 10, q: "Người chịu trách nhiệm chính trong việc thiết kế cấu trúc, quản lí dữ liệu và đảm bảo tính bảo mật của các bảng, mối quan hệ trong một hệ thống là nghề nào sau đây?", opts: { A: "Quản trị mạng.", B: "Lập trình viên Front-end.", C: "Chuyên gia Cơ sở dữ liệu.", D: "Chuyên gia Kiểm thử phần mềm." }, answer: "C" },

  { id: 11, q: "Trong các dự án phát triển phần mềm giáo dục, chuyên viên Công nghệ Thông tin cần thực hiện công việc nào sau đây để giúp phần mềm không ngừng hoàn thiện và mang lại hiệu quả sử dụng cao?", opts: { A: "Phát triển phần mềm mà không cần phản hồi từ người dùng.", B: "Phát triển theo chỉ đạo từ đơn vị quản lý giáo dục.", C: "Dựa vào kinh nghiệm cá nhân để phát triển.", D: "Dựa vào phản hồi của người dùng và cập nhật liên tục." }, answer: "D" },
  { id: 12, q: "Nhóm nghề quản trị trong ngành Công nghệ thông tin KHÔNG liên quan đến công việc nào?", opts: { A: "Quản trị mạng", B: "Bảo mật hệ thống thông tin", C: "Quản trị và bảo trì hệ thống", D: "Phát triển phần mềm" }, answer: "D" },
  { id: 13, q: "Vai trò của quản trị hệ thống mạng trong doanh nghiệp là gì?", opts: { A: "Chỉ cài đặt phần mềm văn phòng", B: "Đảm bảo hệ thống mạng hoạt động ổn định và an toàn", C: "Viết bài quảng cáo trên website", D: "Sửa chữa máy in và máy photocopy" }, answer: "B" },
  { id: 14, q: "Việc nào sau đây KHÔNG thuộc nhóm nghề quản trị trong ngành công nghệ thông tin?", opts: { A: "Quản trị hệ thống mạng", B: "Quản trị cơ sở dữ liệu", C: "Phát triển trò chơi điện tử", D: "An toàn thông tin" }, answer: "C" },
  { id: 15, q: "Kỹ năng quan trọng đối với một quản trị viên hệ thống mạng là gì?", opts: { A: "Chỉ cần biết sử dụng máy tính cơ bản", B: "Hiểu biết về hệ thống mạng, bảo mật và khả năng xử lý sự cố", C: "Chỉ cần kỹ năng giao tiếp", D: "Thiết kế đồ họa chuyên nghiệp" }, answer: "B" },
  { id: 16, q: "Những thách thức chính trong công việc của một quản trị viên an toàn thông tin là gì?", opts: { A: "Cập nhật liên tục các mối đe dọa an ninh mạng và bảo vệ dữ liệu", B: "Lập trình giao diện web", C: "Chỉ cần kiểm tra tốc độ mạng", D: "Viết bài hướng dẫn sử dụng phần mềm" }, answer: "A" },

  { id: 17, q: "Phương án nào sau đây là ngành học phù hợp để theo đuổi nghề quản trị cơ sở dữ liệu?", opts: { A: "Công nghệ thông tin với định hướng quản trị hệ thống.", B: "Khoa học giáo dục với định hướng tâm lý học đường.", C: "Truyền thông đa phương tiện trong lĩnh vực giải trí số.", D: "Ngôn ngữ học với định hướng biên phiên dịch ứng dụng." }, answer: "A" },
  { id: 18, q: "Phương án nào sau đây giúp bạn học sinh lớp 12 chọn đúng ngành học phù hợp năng lực?", opts: { A: "Đánh giá năng lực bản thân, thị trường việc làm, điểm chuẩn.", B: "Chọn ngành theo bạn bè để dễ học nhóm và cùng thi đại học.", C: "Xem điểm chuẩn và chọn ngành có điểm thấp để dễ đậu.", D: "Chọn ngành học theo xu hướng mà không quan tâm sở thích." }, answer: "A" },
  { id: 19, q: "Quân mơ ước trở thành một kỹ sư công nghệ thông tin, nhưng Quân cũng rất đam mê đồ họa. Em hãy giúp Quân chọn ngành học đúng với sở thích của Quân?", opts: { A: "Thiết kế đồ họa.", B: "Quản lí kiểm thử.", C: "Quản trị mạng.", D: "An toàn thông tin." }, answer: "A" },
  { id: 20, q: "Mục đích của hội thảo hướng nghiệp là gì?", opts: { A: "Giúp học sinh chọn trường đại học phù hợp", B: "Định hướng nghề nghiệp và cung cấp thông tin về các ngành nghề", C: "Giới thiệu các phần mềm mới trong ngành IT", D: "Hướng dẫn học sinh cách lập trình" }, answer: "B" },
  { id: 21, q: "Hội thảo hướng nghiệp có thể tổ chức dưới hình thức nào?", opts: { A: "Trực tiếp tại trường học", B: "Hội thảo trực tuyến", C: "Cả trực tiếp và trực tuyến", D: "Chỉ thông qua tài liệu in ấn" }, answer: "C" },
  { id: 22, q: "Ngành nghề nào dưới đây thuộc lĩnh vực công nghệ thông tin?", opts: { A: "Kỹ sư xây dựng", B: "Bác sĩ", C: "Phát triển phần mềm", D: "Luật sư" }, answer: "C" },
  { id: 23, q: "Ngành công nghệ thông tin có xu hướng phát triển như thế nào trong tương lai?", opts: { A: "Giảm nhu cầu do tự động hóa", B: "Ổn định và không thay đổi nhiều", C: "Tăng mạnh do nhu cầu số hóa và AI", D: "Chỉ còn phát triển ở các nước lớn" }, answer: "C" },
  { id: 24, q: "Một trong những yếu tố giúp học sinh chọn ngành nghề phù hợp là gì?", opts: { A: "Đánh giá khả năng và sở thích cá nhân", B: "Chọn nghề theo bạn bè", C: "Chọn nghề dựa trên phim ảnh", D: "Chọn nghề ngẫu nhiên" }, answer: "A" },

  { id: 25, q: "Vì sao học máy (Machine Learning) và xử lí ngôn ngữ tự nhiên (NLP) được xem là hai lĩnh vực quan trọng trong sự phát triển của trí tuệ nhân tạo?", opts: { A: "Vì giúp máy tính tạo ra phần cứng mạnh hơn", B: "Vì giúp máy tính tự học từ dữ liệu và giao tiếp được bằng ngôn ngữ tự nhiên", C: "Vì chỉ tập trung vào xử lí hình ảnh và video", D: "Vì không cần dữ liệu vẫn hoạt động được" }, answer: "B" },
  { id: 26, q: "Đặc trưng của học máy là ý nào sao đây?", opts: { A: "Chương trình máy tính có khả năng phân tích dữ liệu và đưa ra dự đoán dựa trên các quy tắc cụ thể.", B: "Chương trình máy tính có khả năng học từ dữ liệu và đưa ra dự đoán hoặc quyết định mà không cần lập trình cụ thể.", C: "Chương trình máy tính có khả năng thay đổi dữ liệu đầu vào để cải thiện kết quả.", D: "Chương trình máy tính có khả năng tự học và tạo ra các chương trình mới." }, answer: "B" },
  { id: 27, q: "Phương pháp học máy nào sử dụng dữ liệu đã được gán nhãn?", opts: { A: "Học có giám sát", B: "Học không giám sát", C: "Học sâu", D: "Học tăng cường" }, answer: "A" },
  { id: 28, q: "Dữ liệu nào dưới đây thuộc về dữ liệu có nhãn?", opts: { A: "Dữ liệu không có chỉ dẫn về các đặc điểm cần phân loại.", B: "Dữ liệu được gắn với nhãn hoặc giá trị đích cụ thể.", C: "Dữ liệu không có cấu trúc.", D: "Dữ liệu được phân loại theo nhóm nhưng không có mô tả chi tiết." }, answer: "B" },
  { id: 29, q: "Việc chia dữ liệu học máy thành hai phần: dữ liệu huấn luyện và dữ liệu kiểm thử, có mục đích gì?", opts: { A: "Để giảm kích thước dữ liệu huấn luyện.", B: "Để kiểm tra hiệu suất của mô hình trên dữ liệu mới và chưa được học.", C: "Để tránh sự trùng lặp dữ liệu trong quá trình huấn luyện.", D: "Để giảm thời gian huấn luyện mô hình." }, answer: "B" },
  { id: 30, q: "Học máy giúp xây dựng mô hình có thể phân loại thư điện tử thành thư rác hoặc thư hợp lệ. Quá trình này thuộc phương pháp học máy nào?", opts: { A: "Học không giám sát", B: "Học có giám sát", C: "Học sâu", D: "Học tăng cường" }, answer: "B" },
  { id: 31, q: "Tại sao học máy có thể giúp nhận dạng tiếng nói và chữ viết tay?", opts: { A: "Vì học máy có thể lập trình rõ ràng các đặc điểm của từng tiếng nói và chữ viết tay.", B: "Vì học máy giúp máy tính tự học từ dữ liệu để nhận diện các đặc điểm của tiếng nói và chữ viết.", C: "Vì học máy có thể thay đổi dữ liệu âm thanh và hình ảnh để cải thiện kết quả nhận dạng.", D: "Vì học máy có thể nhận diện âm thanh và chữ viết mà không cần dữ liệu." }, answer: "B" },
  { id: 32, q: "Quy trình học máy bao gồm những bước nào?", opts: { A: "Thu thập dữ liệu, chuẩn bị dữ liệu, huấn luyện mô hình, đánh giá mô hình, sử dụng mô hình.", B: "Thu thập dữ liệu, phân tích dữ liệu, sử dụng mô hình, đánh giá kết quả.", C: "Chọn thuật toán, huấn luyện mô hình, phân tích kết quả, cải thiện mô hình.", D: "Thu thập dữ liệu, xử lý dữ liệu, triển khai mô hình, đánh giá kết quả." }, answer: "A" },
  { id: 33, q: "Mô hình học máy được sử dụng để chẩn đoán bệnh. Mô hình này học từ dữ liệu như thế nào?", opts: { A: "Mô hình học từ các triệu chứng bệnh và kết quả xét nghiệm của bệnh nhân để dự đoán và đề xuất phương án điều trị.", B: "Mô hình học từ các bác sĩ để xác định các bệnh lý và phương pháp điều trị.", C: "Mô hình học từ các bản đồ y tế để phân tích tình trạng bệnh.", D: "Mô hình học từ các phương pháp điều trị và kết quả bệnh nhân để dự đoán tỷ lệ hồi phục." }, answer: "A" },
  { id: 34, q: "Khi thiết kế một mô hình học máy để nhận dạng hình ảnh, bạn sẽ làm gì nếu dữ liệu đầu vào chứa nhiều hình ảnh có các đặc điểm khác nhau?", opts: { A: "Lập trình rõ ràng các đặc điểm của đối tượng trong hình ảnh.", B: "Cung cấp cho máy tính hàng nghìn hình ảnh để tự học và nhận dạng các đặc trưng của đối tượng.", C: "Cung cấp chỉ một vài hình ảnh để học máy tự tạo ra quy tắc nhận dạng.", D: "Cung cấp dữ liệu không có nhãn để máy tính tự phân loại." }, answer: "B" },
  { id: 35, q: "Khi sử dụng Học máy để phát hiện gian lận trong các giao dịch thẻ tín dụng, bạn sẽ sử dụng phương pháp học máy nào?", opts: { A: "Học có giám sát với dữ liệu có nhãn là các giao dịch gian lận và hợp lệ.", B: "Học không giám sát với dữ liệu không có nhãn để tìm ra các mẫu gian lận.", C: "Học sâu với dữ liệu được phân loại theo nhóm có sẵn.", D: "Học tăng cường với dữ liệu thử nghiệm về các giao dịch." }, answer: "A" },

  { id: 36, q: "Khoa học dữ liệu là gì?", opts: { A: "Lĩnh vực nghiên cứu các phương pháp xử lý và phân tích dữ liệu để tìm ra tri thức.", B: "Lĩnh vực nghiên cứu các phần mềm quản lý dữ liệu.", C: "Lĩnh vực nghiên cứu về các thuật toán học máy mà không cần dữ liệu.", D: "Lĩnh vực chỉ nghiên cứu về dữ liệu lớn." }, answer: "A" },
  { id: 37, q: "Mục tiêu chính của Khoa học dữ liệu kết quả nào sau đây?", opts: { A: "Thu thập dữ liệu từ nhiều nguồn.", B: "Phân tích và khai phá dữ liệu để đưa ra các quyết định phù hợp.", C: "Lưu trữ dữ liệu trong các cơ sở dữ liệu.", D: "Phân phối dữ liệu cho các tổ chức khác." }, answer: "B" },
  { id: 38, q: "Khoa học dữ liệu sử dụng những công cụ nào để phân tích dữ liệu?", opts: { A: "Khoa học máy tính, toán học và thống kê.", B: "Các công cụ tìm kiếm dữ liệu trên internet.", C: "Công cụ biên tập văn bản.", D: "Các hệ thống quản lý cơ sở dữ liệu." }, answer: "A" },
  { id: 39, q: "Dữ liệu lớn có đặc điểm gì quan trọng?", opts: { A: "Có thể được xử lý dễ dàng và nhanh chóng.", B: "Không có kích thước lớn và dễ phân tích.", C: "Có sự đa dạng về các loại dữ liệu và thường xuyên được cập nhật.", D: "Không thay đổi theo thời gian." }, answer: "C" },
  { id: 40, q: "Khi ứng dụng Khoa học dữ liệu để phân tích hành vi của khách hàng, bạn sẽ sử dụng kỹ thuật nào để phân loại khách hàng thành các nhóm?", opts: { A: "Học có giám sát", B: "Học không giám sát", C: "Học sâu", D: "Học máy hồi quy" }, answer: "B" },

  { id: 41, q: "Trong nhiều lĩnh vực, mô phỏng được ứng dụng để nghiên cứu và thử nghiệm các hệ thống thực trong điều kiện an toàn, tiết kiệm. Phương án nào sau đây phản ánh đúng nhất khái niệm mô phỏng?", opts: { A: "Mô phỏng là quá trình tạo ra một sản phẩm mới không dựa vào hệ thống thực tế", B: "Mô phỏng là phương pháp sao chép nguyên bản hệ thống thực để thay thế hoàn toàn", C: "Mô phỏng là việc sử dụng mô hình ảo để tái hiện hoạt động của hệ thống thực trong điều kiện thử nghiệm", D: "Mô phỏng chỉ được dùng trong lĩnh vực quân sự và hàng không" }, answer: "C" },
  { id: 42, q: "Trong huấn luyện quân sự và giảng dạy y khoa, mô phỏng đã chứng minh hiệu quả rõ rệt trong việc rèn luyện kỹ năng và tiết kiệm chi phí. Cách nào sau đây là lợi ích nổi bật của mô phỏng trong các lĩnh vực này?", opts: { A: "Tái hiện hình ảnh động vật hoang dã trong môi trường tự nhiên", B: "Loại bỏ hoàn toàn nhu cầu sử dụng thiết bị thực tế", C: "Giúp luyện tập và thực hành trong môi trường an toàn, kiểm soát được rủi ro", D: "Thay thế toàn bộ các quy trình huấn luyện truyền thống" }, answer: "C" },
  { id: 43, q: "Trong kỹ thuật, các kỹ sư sử dụng mô phỏng để kiểm tra tính an toàn và hiệu suất sản phẩm mà không cần tạo nguyên mẫu. Câu trả lời nào sau đây thể hiện rõ lợi ích của việc sử dụng mô phỏng trong thiết kế kỹ thuật?", opts: { A: "Đảm bảo mọi thiết kế đều không cần kiểm tra thực tế", B: "Giúp phát hiện lỗi thiết kế và cải tiến sản phẩm trước khi sản xuất", C: "Hạn chế sự sáng tạo do phụ thuộc phần mềm", D: "Giảm độ chính xác so với thử nghiệm thực tế" }, answer: "B" },
  { id: 44, q: "Khi mô phỏng quá trình lan truyền dịch bệnh trong y học, các nhà khoa học có thể điều chỉnh các yếu tố như tốc độ lây lan, mật độ dân cư,… Cách nào sau đây thể hiện đúng nhất lợi ích của khả năng tuỳ chỉnh trong mô phỏng?", opts: { A: "Tăng độ phức tạp của hệ thống cần nghiên cứu", B: "Loại bỏ hoàn toàn việc cần đến chuyên gia", C: "Xác định lỗi phần mềm mô phỏng", D: "Kiểm tra giả thuyết và đưa ra các kịch bản khác nhau để dự đoán tác động thực tế" }, answer: "D" },
  { id: 45, q: "Một giáo viên muốn dạy học sinh về hệ Mặt Trời mà không cần đưa học sinh đến trung tâm thiên văn. Phương án nào sau đây là lựa chọn phù hợp nhất để đạt mục tiêu này bằng mô phỏng?", opts: { A: "Yêu cầu học sinh tự tưởng tượng quỹ đạo các hành tinh", B: "Chiếu phim hoạt hình không tương tác", C: "Sử dụng phần mềm mô phỏng 3D để học sinh quan sát và tương tác với các hành tinh", D: "Chỉ dùng tranh ảnh tĩnh trong sách giáo khoa" }, answer: "C" },
  { id: 46, q: "Một nhà thiết kế trò chơi điện tử muốn tăng tính chân thực và hấp dẫn cho game. Phương án nào sau đây cho thấy cách ứng dụng mô phỏng trong thiết kế trò chơi?", opts: { A: "Tạo ra hình ảnh ảo ngẫu nhiên không cần kịch bản", B: "Mô hình hóa hành vi và phản ứng thực tế của nhân vật và môi trường", C: "Sử dụng hình ảnh đơn giản để giảm tải cho máy tính", D: "Chỉ tập trung phát triển hiệu ứng âm thanh mà không cần mô phỏng hình ảnh" }, answer: "B" },
  { id: 47, q: "Mô phỏng là một kỹ thuật phổ biến được sử dụng trong nhiều lĩnh vực khoa học và đời sống. Phương án nào sau đây là lĩnh vực ít được đề cập trong mô phỏng?", opts: { A: "Y học", B: "Công nghiệp giải trí", C: "Tài chính kế toán", D: "Giáo dục" }, answer: "C" },
  { id: 48, q: "Việc sử dụng phần mềm để tạo mô hình ảo nhằm khảo sát hoặc dự đoán cách hệ thống thực hoạt động là một ví dụ của mô phỏng. Phương án nào sau đây mô tả đúng về vai trò của phần mềm trong mô phỏng?", opts: { A: "Phần mềm chỉ đóng vai trò minh họa hình ảnh tĩnh", B: "Phần mềm mô phỏng giúp tạo ra mô hình ảo tương tác để nghiên cứu và đào tạo", C: "Phần mềm chỉ dùng trong quân sự và hàng không", D: "Phần mềm mô phỏng thay thế toàn bộ hoạt động thực tế" }, answer: "B" },
  { id: 49, q: "Trong giáo dục, mô phỏng giúp học sinh tiếp cận kiến thức một cách trực quan, sinh động. Cách nào sau đây thể hiện đúng nhất lợi ích của mô phỏng trong dạy học?", opts: { A: "Làm thay giáo viên trong mọi hoạt động giảng dạy", B: "Tăng độ khó của bài học để kiểm tra năng lực học sinh", C: "Cho phép học sinh thực hành các tình huống phức tạp trong môi trường an toàn", D: "Làm cho học sinh phụ thuộc hoàn toàn vào máy tính" }, answer: "C" },
  { id: 50, q: "Trong thực tế, mô phỏng giúp tiết kiệm chi phí và giảm thiểu rủi ro so với thử nghiệm trực tiếp trên hệ thống thật. Phương án nào sau đây là lý do hợp lý để sử dụng mô phỏng thay cho thử nghiệm thực tế?", opts: { A: "Mô phỏng cho kết quả đẹp hơn thực tế", B: "Thử nghiệm thực tế luôn kém chính xác hơn", C: "Mô phỏng luôn dễ dàng hơn bất kỳ cách tiếp cận nào khác", D: "Thử nghiệm thực tế có thể tốn kém, nguy hiểm hoặc không khả thi" }, answer: "D" },
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
