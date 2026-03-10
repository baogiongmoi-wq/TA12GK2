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
{id:1, answer:"A", q:"Many companies use AI to analyze large amounts of _____ more efficiently.", opts:{A:"data",B:"noise",C:"water",D:"pollution"}},
{id:2, answer:"C", q:"Facial recognition systems can identify individuals by analyzing their unique _____ features.", opts:{A:"digital",B:"artificial",C:"physical",D:"virtual"}},
{id:3, answer:"D", q:"Cyber-bullying is popular online, causing emotional______, and even leads to suicide.", opts:{A:"stimulation",B:"motivation",C:"excitement",D:"disorder"}},
{id:4, answer:"A", q:"One concern about AI development is the potential loss of human _____.", opts:{A:"employment",B:"happiness",C:"culture",D:"language"}},
{id:5, answer:"B", q:"Students who _____ social media so much can lose the ability to think critically.", opts:{A:"give up",B:"rely on",C:"separate from",D:"split into"}},

{id:6, answer:"B", q:"Some experts believe that AI will greatly _____ human capabilities in the future.", opts:{A:"replace",B:"enhance",C:"remove",D:"delete"}},
{id:7, answer:"C", q:"Ethical guidelines are necessary to ensure the responsible _____ of AI.", opts:{A:"disappearance",B:"reduction",C:"development",D:"avoidance"}},
{id:8, answer:"A", q:"Using social networks helps you _____ in touch with friends and family members any time.", opts:{A:"keep",B:"lose",C:"have",D:"make"}},
{id:9, answer:"A", q:"In the early 21st century, with the _____ of mobile communication technology, the mobile phone has emerged as a new and unique channel.", opts:{A:"explosion",B:"explanation",C:"exploitation",D:"exploration"}},
{id:10, answer:"D", q:"I haven’t read any medical books or articles on this subject for a long time, so I’m _____ with recent developments.", opts:{A:"out of condition",B:"out of reach",C:"out of date",D:"out of touch"}},

{id:11, answer:"B", q:"The mass media are _____ of communication, such as books, newspapers, recordings, radio, movies, television, mobile phones and the Internet.", opts:{A:"models",B:"means",C:"parts",D:"types"}},
{id:12, answer:"C", q:"Teens can become _____ social networking if they can’t control the time they spend online.", opts:{A:"separated from",B:"indifferent of",C:"addicted to",D:"exhausted by"}},
{id:13, answer:"B", q:"Watching short videos on the Internet is a common form of _____ among teenagers.", opts:{A:"stress",B:"entertainment",C:"pressure",D:"effort"}},
{id:14, answer:"C", q:"Experts are increasingly _____ about the negative effects of excessive screen time.", opts:{A:"confident",B:"relaxed",C:"worried",D:"delighted"}},
{id:15, answer:"D", q:"Volunteers help _____ awareness about endangered species in local communities.", opts:{A:"life",B:"rise",C:"grow",D:"raise"}},

{id:16, answer:"B", q:"Because forests are being cleared for agriculture, many animals are losing their natural _____, which threatens their survival.", opts:{A:"ecosystem",B:"habitat",C:"biodiversity",D:"balance"}},
{id:17, answer:"D", q:"Scientists warn that without immediate action, several endangered species may become _____ within the next few decades.", opts:{A:"invasive",B:"protected",C:"sustainable",D:"extinct"}},
{id:18, answer:"C", q:"Illegal hunting and wildlife trade are major causes of species decline, especially in regions where laws are not strictly _____.", opts:{A:"raised",B:"conserved",C:"enforced",D:"preserved"}},
{id:19, answer:"A", q:"Many marine animals are at risk due to _____, which reduces fish populations faster than they can reproduce.", opts:{A:"overfishing",B:"conservation",C:"restoration",D:"participation"}},
{id:20, answer:"A", q:"If habitat fragmentation continues, many species will be isolated in small areas, leading to a serious loss of _____.", opts:{A:"biodiversity",B:"tourism",C:"emission",D:"farming"}},

{id:21, answer:"B", q:"Climate change has increased the frequency of natural _____ such as forest fires and severe storms.", opts:{A:"predators",B:"disasters",C:"emissions",D:"resources"}},
{id:22, answer:"C", q:"Captive breeding programs aim to increase the population of critically _____ species.", opts:{A:"expanding",B:"surviving",C:"endangered",D:"hunting"}},
{id:23, answer:"B", q:"Governments must _____ immediate action to prevent further environmental damage.", opts:{A:"make",B:"take",C:"do",D:"give"}},
{id:24, answer:"D", q:"AI systems can work more _____ than humans in repetitive tasks.", opts:{A:"inefficient",B:"efficiency",C:"efficient",D:"efficiently"}},
{id:25, answer:"B", q:"Many experts are concerned about the _____ use of AI in surveillance.", opts:{A:"responsible",B:"irresponsible",C:"responsibility",D:"responsibly"}},

{id:26, answer:"D", q:"Scientists are working _____ to improve AI accuracy.", opts:{A:"constant",B:"inconstant",C:"constancy",D:"constantly"}},
{id:27, answer:"C", q:"Climate change has had a significant _____ on marine ecosystems worldwide.", opts:{A:"affect",B:"affecting",C:"effect",D:"effective"}},
{id:28, answer:"D", q:"The law was strictly _____ to prevent illegal wildlife trade.", opts:{A:"enforcement",B:"enforcing",C:"enforce",D:"enforced"}},
{id:29, answer:"B", q:"Environmental _____ should be included in school curricula to educate young people.", opts:{A:"aware",B:"awareness",C:"awarely",D:"unaware"}},
{id:30, answer:"B", q:"Poachers are often unaware of the _____ consequences of their actions.", opts:{A:"destroy",B:"destructive",C:"destructively",D:"destruction"}},

{id:31, answer:"A", q:"Companies often _____ their IT teams upgrade AI systems regularly.", opts:{A:"have",B:"get",C:"make",D:"do"}},
{id:32, answer:"A", q:"The manager had the technicians _____ the AI software immediately.", opts:{A:"install",B:"installed",C:"installing",D:"to install"}},
{id:33, answer:"D", q:"The company will get a specialist _____ the security system.", opts:{A:"check",B:"checked",C:"checking",D:"to check"}},
{id:34, answer:"B", q:"Many organizations have their data _____ by AI experts.", opts:{A:"analyze",B:"analyzed",C:"analyzing",D:"to analyze"}},
{id:35, answer:"A", q:"The government will have experts _____ the ethical risks of AI.", opts:{A:"assess",B:"assessed",C:"assessing",D:"to assess"}},

{id:36, answer:"C", q:"He talks about television production as though he _____ a professional producer, but he has never worked in media.", opts:{A:"is",B:"was",C:"were",D:"has been"}},
{id:37, answer:"B", q:"He gives advice about journalism as though he _____ many years of experience, but he graduated only last month.", opts:{A:"has",B:"had",C:"having",D:"has had"}},
{id:38, answer:"B", q:"The blogger talks as if he _____ the CEO personally, but he has never met him.", opts:{A:"knows",B:"knew",C:"known",D:"knowing"}},
{id:39, answer:"B", q:"The news report was _____ shocking that millions of viewers shared it on social media immediately.", opts:{A:"such",B:"so",C:"very",D:"too"}},
{id:40, answer:"C", q:"The journalist gave _____ detailed explanation that the audience understood the issue clearly.", opts:{A:"so",B:"such",C:"such a",D:"so a"}},

{id:41, answer:"D", q:"The television program was _____ popular that it attracted viewers from all over the country.", opts:{A:"such",B:"very",C:"such a",D:"so"}},
{id:42, answer:"C", q:"It was _____ influential documentary that it changed many people’s opinions.", opts:{A:"so",B:"such",C:"such an",D:"so an"}},
{id:43, answer:"B", q:"The online article contained _____ misleading information that many readers believed it.", opts:{A:"so",B:"such",C:"such a",D:"so a"}},
{id:44, answer:"A", q:"If people continue cutting down forests, many animals _____ their natural habitats.", opts:{A:"will lose",B:"lose",C:"lost",D:"would lose"}},
{id:45, answer:"D", q:"If we reduce greenhouse gas emissions, global temperatures _____ more slowly.", opts:{A:"rise",B:"would rise",C:"rose",D:"will rise"}},

{id:46, answer:"C", q:"Unless stricter laws are enforced, illegal hunting _____ significantly.", opts:{A:"decreases",B:"will decrease",C:"won’t decrease",D:"would decrease"}},
{id:47, answer:"D", q:"She takes an umbrella with her _____ it rains on the way home.", opts:{A:"unless",B:"if",C:"provided that",D:"in case"}},
{id:48, answer:"A", q:"Marine ecosystems are often _____ fragile than forest ecosystems due to pollution and climate change.", opts:{A:"more",B:"most",C:"as",D:"very"}},
{id:49, answer:"D", q:"Air pollution in urban areas is becoming _____ serious than it was a decade ago.", opts:{A:"so",B:"most",C:"very",D:"more"}},
{id:50, answer:"C", q:"Noise pollution in the countryside is not _____ that in the city.", opts:{A:"serious",B:"more serious",C:"as serious as",D:"most serious"}}
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
