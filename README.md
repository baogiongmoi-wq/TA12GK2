<!doctype html>
<html lang="vi">
<head>
  <meta charset="utf-8">
  <meta name="viewport" content="width=device-width,initial-scale=1">
  <title>Vocabulary & Grammar Test - 50 Questions</title>
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
      <h1>Vocabulary & Grammar - 50-question Test</h1>
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
    q: "Router là còn được gọi là gì trong các đáp án sau đây?",
    opts: {
      A: "Bộ chuyển mạch.",
      B: "Bộ thu phát không dây.",
      C: "Bộ định tuyến.",
      D: "Bộ chia tín hiệu."
    },
    answer: "C"
  },
  {
    id: 2,
    q: "Trên mỗi router, cổng để kết nối với các router khác được gọi là cổng nào trong các đáp án sau?",
    opts: {
      A: "Cổng WAP.",
      B: "Cổng WAN.",
      C: "Cổng LAN.",
      D: "Cổng AP."
    },
    answer: "B"
  },
  {
    id: 3,
    q: "Loại modem nào sau đây cho phép nối hai máy tính qua hệ thống chuyển mạch của mạng điện thoại công cộng?",
    opts: {
      A: "Modem quay số.",
      B: "Modem GSM 3G, 4G, 5G,…",
      C: "Modem ADSL.",
      D: "Modem quang."
    },
    answer: "A"
  },
  {
    id: 4,
    q: "Khi kết nối hai máy tính (có thể cách xa hàng nghìn kilômét) qua Internet, người ta sử dụng thiết bị nào sau đây để kết nối các LAN với nhau?",
    opts: {
      A: "Hub.",
      B: "Wireless Access Point.",
      C: "Switch.",
      D: "Router."
    },
    answer: "D"
  },
  {
    id: 5,
    q: "Thiết bị nào sau đây đóng vai trò trung tâm trong một mạng LAN có dây?",
    opts: {
      A: "Router",
      B: "Switch",
      C: "Modem",
      D: "Access Point"
    },
    answer: "B"
  },
  {
    id: 6,
    q: "Switch khác với Hub khác nhau ở điểm nào sau đây?",
    opts: {
      A: "Switch chỉ kết nối hai máy tính, còn Hub kết nối nhiều máy tính",
      B: "Switch thông minh hơn, chỉ gửi dữ liệu đến thiết bị cần nhận",
      C: "Hub có thể kết nối Internet, còn Switch không thể",
      D: "Hub hoạt động ở tầng mạng, còn Switch hoạt động ở tầng ứng dụng"
    },
    answer: "B"
  },
  {
    id: 7,
    q: "Thiết bị nào sau đây có nhiệm vụ khuếch đại và mở rộng phạm vi tín hiệu mạng?",
    opts: {
      A: "Repeater",
      B: "Router",
      C: "Switch",
      D: "Modem"
    },
    answer: "A"
  },
  {
    id: 8,
    q: "Đáp án nào sau đây KHÔNG phải là thông số kĩ thuật của một router?",
    opts: {
      A: "Tốc độ truyền dữ liệu qua các cổng",
      B: "Số lượng truy cập đồng thời",
      C: "Loại cáp được sử dụng",
      D: "Số cổng kết nối"
    },
    answer: "C"
  },
  {
    id: 9,
    q: "Wireless Access Point (WAP) có chức năng nào sau đây?",
    opts: {
      A: "Chuyển đổi tín hiệu từ tín hiệu số sang tín hiệu tương tự và ngược lại, thường dùng khi kết nối LAN với Internet.",
      B: "Dùng để kết nối các máy tính trong cùng LAN trực tiếp qua cáp mạng.",
      C: "Dùng để kết nối các thiết bị đầu cuối qua sóng Wi-Fi giúp giảm chi phí thiết lập LAN hoặc kết nối với một LAN để mở rộng phạm vi làm việc.",
      D: "Dùng để dẫn đường cho dữ liệu khi kết nối trên mạng diện rộng như Internet."
    },
    answer: "C"
  },
  {
    id: 10,
    q: "Khi kết nối máy tính với các thiết bị mạng, cần cắm một đầu giắc của cáp vào cổng nào sau đây của máy tính?",
    opts: {
      A: "RJ45.",
      B: "VJ45.",
      C: "CJ45.",
      D: "PJ45."
    },
    answer: "A"
  },
  {
    id: 11,
    q: "Hiện nay có những loại địa chỉ IP nào sau đây?",
    opts: {
      A: "IPv4 và IPv6.",
      B: "IPv2 và IPv4.",
      C: "IPv4 và IPv5.",
      D: "IPv1 và IPv3."
    },
    answer: "A"
  },
  {
    id: 12,
    q: "Việc truyền dữ liệu trong mạng cục bộ sẽ căn cứ vào địa chỉ nào trong các địa chỉ sau?",
    opts: {
      A: "Địa chỉ IP.",
      B: "Địa chỉ MAC.",
      C: "Địa chỉ LAN.",
      D: "Địa chỉ Server."
    },
    answer: "B"
  },
  {
    id: 13,
    q: "Giao thức quy định cách biểu diễn (mã hoá) các trang web là giao thức nào sau đây?",
    opts: {
      A: "SNMP.",
      B: "DNS.",
      C: "HTTP.",
      D: "DHCP."
    },
    answer: "C"
  },
  {
    id: 14,
    q: "Địa chỉ IP 11001011 10100010 00101001 11111110 dưới dạng thập phân là đáp án nào sau đây?",
    opts: {
      A: "203.162.41.254.",
      B: "230.178.52.166.",
      C: "203.126.71.235.",
      D: "235.197.80.255."
    },
    answer: "A"
  },
  {
    id: 15,
    q: "Thiết bị nào sau đây có chức năng chính là để kết nối không dây trong một mạng cục bộ?",
    opts: {
      A: "Router.",
      B: "Switch.",
      C: "Hub.",
      D: "Access Point."
    },
    answer: "D"
  },
  {
  id: 16,
  q: "Phương tiện truyền dẫn nào sau đây sử dụng tín hiệu ánh sáng để truyền dữ liệu?",
  opts: {
    A: "Cáp xoắn đôi",
    B: "Cáp đồng trục",
    C: "Cáp quang",
    D: "Bluetooth"
  },
  answer: "C"
},
{
  id: 17,
  q: "Loại cáp nào sau đây thường được sử dụng phổ biến trong mạng LAN có dây?",
  opts: {
    A: "Cáp quang",
    B: "Cáp đồng trục",
    C: "Cáp xoắn đôi",
    D: "Bluetooth"
  },
  answer: "C"
},
{
  id: 18,
  q: "Bluetooth là công nghệ kết nối không dây có đặc điểm nào sau đây?",
  opts: {
    A: "Tốc độ truyền dữ liệu cao hơn cáp quang",
    B: "Phạm vi truyền dữ liệu ngắn, khoảng vài mét",
    C: "Dùng để kết nối mạng LAN tốc độ cao",
    D: "Yêu cầu sử dụng cáp để truyền tín hiệu"
  },
  answer: "B"
},
{
  id: 19,
  q: "Đáp án nào sau đây KHÔNG thể dùng kết nối Bluetooth?",
  opts: {
    A: "Điện thoại di động với loa",
    B: "Điện thoại di động với điện thoại di động",
    C: "Máy in với loa",
    D: "Máy tính với máy in"
  },
  answer: "C"
},
{
  id: 20,
  q: "LAN là loại mạng nào sau đây?",
  opts: {
    A: "Mạng cục bộ.",
    B: "Mạng diện rộng.",
    C: "Mạng toàn cầu.",
    D: "Mạng thành phố."
  },
  answer: "A"
},
{
  id: 21,
  q: "Modem có chức năng gì nào sau đây trong mạng máy tính?",
  opts: {
    A: "Chuyển đổi tín hiệu số thành tín hiệu tương tự và ngược lại.",
    B: "Kết nối các máy tính trong mạng nội bộ.",
    C: "Điều khiển truy cập mạng.",
    D: "Lưu trữ dữ liệu."
  },
  answer: "A"
},
{
  id: 22,
  q: "Khẳng định nào sau đây ĐÚNG khi nói về giao thức mạng?",
  opts: {
    A: "Một ngôn ngữ lập trình.",
    B: "Một loại phần mềm diệt virus.",
    C: "Bộ quy tắc và tiêu chuẩn dùng để truyền tải dữ liệu qua mạng.",
    D: "Một loại phần cứng mạng."
  },
  answer: "C"
},
{
  id: 23,
  q: "Giao thức nào sau đây được sử dụng để bảo mật các giao dịch trên web?",
  opts: {
    A: "HTTP.",
    B: "FTP.",
    C: "HTTPS.",
    D: "SMTP."
  },
  answer: "C"
},
{
  id: 24,
  q: "Phát biểu nào sau đây ĐÚNG khi nói về mạng máy tính?",
  opts: {
    A: "Giao thức TCP quy định cách thiết lập địa chỉ cho các thiết bị tham gia mạng và cách dẫn đường các gói dữ liệu theo địa chỉ từ thiết bị gửi đến thiết bị nhận.",
    B: "Phương pháp định tuyến tĩnh cho phép có thể thay đổi cổng gửi đi tuỳ thuộc vào điều kiện cụ thể.",
    C: "Các gói tin gửi đi trên Internet luôn phải được gán địa chỉ IP của máy tính gửi và máy tính nhận.",
    D: "Giao thức HTTP (Hypertext Transfer Protocol) cho phép dùng hệ thống tên bằng chữ thay thế cho địa chỉ IP vốn khó nhớ."
  },
  answer: "C"
},
{
  id: 25,
  q: "Để chia sẻ một thư mục trên mạng nội bộ, ta cần thực hiện thao tác nào sau đây trong Windows?",
  opts: {
    A: "Nhấp chuột phải vào thư mục, chọn “Properties”, sau đó chọn tab “Sharing”.",
    B: "Nhấp chuột phải vào thư mục, chọn “Delete”.",
    C: "Mở thư mục bằng Windows Media Player.",
    D: "Nhấp chuột phải vào thư mục, chọn “Cut”."
  },
  answer: "A"
},
{
  id: 26,
  q: "Đâu là mục đích chính của dịch vụ sửa chữa và bảo trì máy tính trong các phương án sau:",
  opts: {
    A: "Làm cho máy tính chạy nhanh hơn bình thường",
    B: "Duy trì sự ổn định của máy tính cũng như các thiết bị có liên quan tới máy tính",
    C: "Chỉ để nâng cấp phần mềm trên máy tính",
    D: "Chỉ thay thế linh kiện phần cứng khi hỏng hóc"
  },
  answer: "B"
},
{
  id: 27,
  q: "Với người làm nghề sửa chữa và bảo trì máy tính thì những việc nào sau đâu KHÔNG liên quan đến phần cứng:",
  opts: {
    A: "Kiểm soát và duy trì hoạt động của máy tính",
    B: "Đảm bảo kết nối máy tính vào mạng",
    C: "Lắp đặt, sửa chữa hoặc thay thế các linh kiện máy tính bị hỏng",
    D: "Xác định và khắc phục lỗi phần cứng khi có sự cố xảy ra"
  },
  answer: "B"
},
{
  id: 28,
  q: "Với người làm nghề sửa chữa và bảo trì máy tính thì những việc nào sau đâu KHÔNG liên quan đến phần mềm:",
  opts: {
    A: "Cài đặt hoặc cập nhật phần điều khiển thiết bị ngoại vi",
    B: "Đảm bảo kết nối máy tính vào mạng",
    C: "Cập nhật các phiên bản mới của phần mềm để đảm bảo tính an toàn và hiệu quả",
    D: "Phát hiện nguyên nhân hỏng thiết bị để biết liệu có thể sửa, thay thế hay cấu hình lại"
  },
  answer: "D"
},
{
  id: 29,
  q: "Với người làm nghề sửa chữa và bảo trì máy tính thì việc theo dõi, cập nhật để có hiểu biết về công nghệ mới là kĩ năng nào trong các kĩ năng sau:",
  opts: {
    A: "Kĩ năng học hỏi, cập nhật kiến thức",
    B: "Kĩ năng giải quyết vấn đề",
    C: "Kĩ năng giao tiếp",
    D: "Kĩ năng quản lí thười gian"
  },
  answer: "A"
},
{
  id: 30,
  q: "Nguyên lí hoạt động của máy tính và thiết bị công nghệ thông tin được đào tạo nhiều ở bậc học nào sau đây:",
  opts: {
    A: "Cao học",
    B: "Đại học",
    C: "Cao đẳng",
    D: "Trung cấp nghề"
  },
  answer: "B"
},
{
  id: 31,
  q: "Nhóm nghề quản trị trong ngành Công nghệ thông tin KHÔNG liên quan đến công việc nào?",
  opts: {
    A: "Quản trị mạng",
    B: "Bảo mật hệ thống thông tin",
    C: "Quản trị và bảo trì hệ thống",
    D: "Phát triển phần mềm"
  },
  answer: "D"
},
{
  id: 32,
  q: "Vai trò của quản trị hệ thống mạng trong doanh nghiệp là gì?",
  opts: {
    A: "Chỉ cài đặt phần mềm văn phòng",
    B: "Đảm bảo hệ thống mạng hoạt động ổn định và an toàn",
    C: "Viết bài quảng cáo trên website",
    D: "Sửa chữa máy in và máy photocopy"
  },
  answer: "B"
},
{
  id: 33,
  q: "Việc nào sau đây KHÔNG thuộc nhóm nghề quản trị trong ngành công nghệ thông tin?",
  opts: {
    A: "Quản trị hệ thống mạng",
    B: "Quản trị cơ sở dữ liệu",
    C: "Phát triển trò chơi điện tử",
    D: "An toàn thông tin"
  },
  answer: "C"
},
{
  id: 34,
  q: "Kỹ năng quan trọng đối với một quản trị viên hệ thống mạng là gì?",
  opts: {
    A: "Chỉ cần biết sử dụng máy tính cơ bản",
    B: "Hiểu biết về hệ thống mạng, bảo mật và khả năng xử lý sự cố",
    C: "Chỉ cần kỹ năng giao tiếp",
    D: "Thiết kế đồ họa chuyên nghiệp"
  },
  answer: "B"
},
{
  id: 35,
  q: "Những thách thức chính trong công việc của một quản trị viên an toàn thông tin là gì?",
  opts: {
    A: "Cập nhật liên tục các mối đe dọa an ninh mạng và bảo vệ dữ liệu",
    B: "Lập trình giao diện web",
    C: "Chỉ cần kiểm tra tốc độ mạng",
    D: "Viết bài hướng dẫn sử dụng phần mềm"
  },
  answer: "A"
},
{
  id: 36,
  q: "Mục đích của hội thảo hướng nghiệp là gì?",
  opts: {
    A: "Giúp học sinh chọn trường đại học phù hợp",
    B: "Định hướng nghề nghiệp và cung cấp thông tin về các ngành nghề",
    C: "Giới thiệu các phần mềm mới trong ngành IT",
    D: "Hướng dẫn học sinh cách lập trình"
  },
  answer: "B"
},
{
  id: 37,
  q: "Hội thảo hướng nghiệp có thể tổ chức dưới hình thức nào?",
  opts: {
    A: "Trực tiếp tại trường học",
    B: "Hội thảo trực tuyến",
    C: "Cả trực tiếp và trực tuyến",
    D: "Chỉ thông qua tài liệu in ấn"
  },
  answer: "C"
},
{
  id: 38,
  q: "Ngành nghề nào dưới đây thuộc lĩnh vực công nghệ thông tin?",
  opts: {
    A: "Kỹ sư xây dựng",
    B: "Bác sĩ",
    C: "Phát triển phần mềm",
    D: "Luật sư"
  },
  answer: "C"
},
{
  id: 39,
  q: "Ngành công nghệ thông tin có xu hướng phát triển như thế nào trong tương lai?",
  opts: {
    A: "Giảm nhu cầu do tự động hóa",
    B: "Ổn định và không thay đổi nhiều",
    C: "Tăng mạnh do nhu cầu số hóa và AI",
    D: "Chỉ còn phát triển ở các nước lớn"
  },
  answer: "C"
},
{
  id: 40,
  q: "Một trong những yếu tố giúp học sinh chọn ngành nghề phù hợp là gì?",
  opts: {
    A: "Đánh giá khả năng và sở thích cá nhân",
    B: "Chọn nghề theo bạn bè",
    C: "Chọn nghề dựa trên phim ảnh",
    D: "Chọn nghề ngẫu nhiên"
  },
  answer: "A"
}
];
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
