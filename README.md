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
    q: "Khi điện phân NaCl nóng chảy (điện cực trơ), ở cathode xảy ra?",
    opts: { A: "Sự khử ion Cl-", B: "Sự oxi hóa ion Cl-", C: "Sự oxi hóa ion Na+", D: "Sự khử ion Na+" },
    answer: "D"
  },
  {
    id: 2,
    q: "Dãy nào sau đây sắp xếp các kim loại nhóm IA theo mức độ phản ứng với nước tăng dần?",
    opts: { A: "K, Na, Li", B: "Na, K, Li", C: "Li, Na, K", D: "K, Li, Na" },
    answer: "C"
  },
  {
    id: 3,
    q: "Để bảo quản kim loại kiềm lâu dài, chúng thường được ngâm trong",
    opts: { A: "dầu hoả", B: "nước máy", C: "ethyl alcohol", D: "giấm ăn" },
    answer: "A"
  },
  {
    id: 4,
    q: "Dãy nào sau đây sắp xếp các dung dịch (cùng nồng độ 0,1 M) theo thứ tự pH giảm dần?",
    opts: { A: "LiOH, Na2CO3, KCl", B: "Na2CO3, KCl, LiOH", C: "KCl, Na2CO3, LiOH", D: "Na2CO3, LiOH, KCl" },
    answer: "A"
  },
  {
    id: 5,
    q: "Cấu hình electron của Fe2+ là",
    opts: { A: "[Ar]3d6 4s2", B: "[Ar]3d5", C: "[Ar]3d6", D: "[Ar]3d4 4s1" },
    answer: "C"
  },
  {
    id: 6,
    q: "Số lượng phối tử có trong phức chất [PtCl4(NH3)2] là",
    opts: { A: "6", B: "2", C: "4", D: "7" },
    answer: "A"
  },
  {
    id: 7,
    q: "Dãy các kim loại đều có thể được điều chế bằng phương pháp điện phân dung dịch muối của chúng là:",
    opts: { A: "Fe, Cu, Ag", B: "Mg, Zn, Cu", C: "Al, Fe, Cr", D: "Ba, Ag, Au" },
    answer: "A"
  },
  {
    id: 8,
    q: "Phát biểu nào sau đây không đúng?",
    opts: {
      A: "Các nguyên tố kim loại chuyển tiếp dãy thứ nhất thuộc khối d",
      B: "Zn là nguyên tử kim loại chuyển tiếp dãy thứ nhất duy nhất có phân lớp 3d đã điền đầy electron",
      C: "Nguyên tử của các kim loại chuyển tiếp dãy thứ nhất đều có lớp vỏ bên trong của khí hiếm Ar",
      D: "Kim loại chuyển tiếp dãy thứ nhất thường tạo hợp chất với nhiều số oxi hoá khác nhau"
    },
    answer: "B"
  },
  {
    id: 9,
    q: "Kim loại nào sau đây điều chế được bằng phương pháp thủy luyện?",
    opts: { A: "Mg", B: "Ca", C: "Cu", D: "K" },
    answer: "C"
  },
  {
    id: 10,
    q: "Nguyên tử trung tâm của phức chất [PtCl4]2- và [Fe(CO)5] lần lượt là",
    opts: { A: "Pt4+ và Fe2+", B: "Pt2+ và Fe2+", C: "Cl và CO", D: "Pt2+ và Fe" },
    answer: "D"
  },
  {
    id: 11,
    q: "Kim loại nào sau đây khi tác dụng với dung dịch HCl và khí Cl2 (t°) cho cùng một loại muối?",
    opts: { A: "bạc", B: "sắt", C: "đồng", D: "magie" },
    answer: "D"
  },
  {
    id: 12,
    q: "Nhỏ vài giọt dung dịch phenolphthalein vào dung dịch Na2CO3 thì dung dịch chuyển sang màu",
    opts: { A: "tím", B: "vàng", C: "xanh", D: "hồng" },
    answer: "D"
  },
  {
    id: 13,
    q: "Tổng số proton và electron của ion Mg2+ là",
    opts: { A: "26", B: "24", C: "22", D: "12" },
    answer: "C"
  },
  {
    id: 14,
    q: "Phức chất tạo thành khi thay toàn bộ H2O bằng NH3 trong [Ni(H2O)6]2+ là",
    opts: {
      A: "[Ni(NH3)6]2+",
      B: "[Ni(NH3)2(H2O)4]",
      C: "[Ni(NH3)(H2O)5]2+",
      D: "[Ni(NH3)5(H2O)]2+"
    },
    answer: "A"
  },
  {
    id: 15,
    q: "Nước cứng là nước có chứa nhiều ion",
    opts: { A: "Mg2+ và Ca2+", B: "Na+ và K+", C: "F- và Cl-", D: "SO4^2- và CO3^2-" },
    answer: "A"
  },
  {
    id: 16,
    q: "Kim loại nào sau đây có nhiệt độ nóng chảy thấp nhất?",
    opts: { A: "Li", B: "Cu", C: "Ag", D: "Hg" },
    answer: "D"
  },
  {
    id: 17,
    q: "Nguyên tố Ca thuộc nhóm nào?",
    opts: { A: "IIIA", B: "IA", C: "IVA", D: "IIA" },
    answer: "D"
  },
  {
    id: 18,
    q: "Phát biểu đúng về các phức chất [PtCl2(NH3)4]2+ và [FeF6]3- là",
    opts: {
      A: "Số lượng phối tử lần lượt là 4 và 6",
      B: "Điện tích lần lượt là +4 và +3",
      C: "Nguyên tử trung tâm là Pt4+ và Fe3+",
      D: "Cả hai đều ít tan trong nước"
    },
    answer: "C"
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
