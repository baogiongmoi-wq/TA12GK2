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
    q: "Many scientists are excited because modern robots can ______ human emotions through facial recognition systems.",
    opts: { A: "understand", B: "repair", C: "arrange", D: "interrupt" },
    answer: "A"
  },
  {
    id: 2,
    q: "Online platforms, which are becoming more popular nowadays, ______ learning for students who live in remote or mountainous areas.",
    opts: { A: "prevent", B: "limit", C: "delay", D: "support" },
    answer: "D"
  },
  {
    id: 3,
    q: "Artificial intelligence can help doctors ______ diseases at an early stage, improving patients’ chances of recovery significantly.",
    opts: { A: "create", B: "detect", C: "destroy", D: "avoid" },
    answer: "B"
  },
  {
    id: 4,
    q: "Some people worry about the ______ of AI on employment, especially when robots replace human workers in repetitive tasks.",
    opts: { A: "exploration", B: "feedback", C: "impact", D: "appearance" },
    answer: "C"
  },
  {
    id: 5,
    q: "Spending too much time on social media can cause serious ______ and reduce study effectiveness.",
    opts: { A: "distraction", B: "determination", C: "opportunity", D: "intelligence" },
    answer: "A"
  },
  {
    id: 6,
    q: "AI software can process complex data ______, which allows companies to make decisions more quickly and accurately.",
    opts: { A: "carelessly", B: "slowly", C: "badly", D: "efficiently" },
    answer: "D"
  },
  {
    id: 7,
    q: "Many companies use social media platforms to ______ their products effectively and reach a wider audience worldwide.",
    opts: { A: "promote", B: "confuse", C: "struggle", D: "assume" },
    answer: "A"
  },
  {
    id: 8,
    q: "Advertisements on digital media are often more ______ than traditional posters because they can attract more viewers.",
    opts: { A: "informative", B: "persuasive", C: "effective", D: "creative" },
    answer: "C"
  },
  {
    id: 9,
    q: "The new application is very ______ for users who want to save time and manage their work efficiently.",
    opts: { A: "inconvenient", B: "convenient", C: "harmful", D: "tiring" },
    answer: "B"
  },
  {
    id: 10,
    q: "Journalists must always ______ information carefully before publishing articles to ensure accuracy and credibility.",
    opts: { A: "fact-check", B: "broadcast", C: "collect", D: "report" },
    answer: "A"
  },
  {
    id: 11,
    q: "Many organizations use social media to ______ people to take part in volunteer activities and support the community.",
    opts: { A: "refuse", B: "avoid", C: "ignore", D: "encourage" },
    answer: "D"
  },
  {
    id: 12,
    q: "News reports are now ______ to most people thanks to smartphones and other electronic devices.",
    opts: { A: "accessible", B: "reachable", C: "limited", D: "convenient" },
    answer: "A"
  },
  {
    id: 13,
    q: "The authorities are working hard to ______ endangered species and prevent them from becoming extinct in the future.",
    opts: { A: "bury", B: "conserve", C: "prohibit", D: "vanish" },
    answer: "B"
  },
  {
    id: 14,
    q: "Deforestation is one of the main causes of the rapid ______ of wildlife populations in tropical rainforests.",
    opts: { A: "growth", B: "stability", C: "increase", D: "decrease" },
    answer: "D"
  },
  {
    id: 15,
    q: "Many endangered animals in Canada have been protected within wildlife ____ for a long time.",
    opts: { A: "reserves", B: "disasters", C: "habitats", D: "stations" },
    answer: "A"
  },
  {
    id: 16,
    q: "Marine biologists are trying to protect coral ______ because they are important for biodiversity and ecosystem balance.",
    opts: { A: "fish", B: "animals", C: "reefs", D: "plants" },
    answer: "C"
  },
  {
    id: 17,
    q: "Many rare species are now considered ______ because their natural habitats are being destroyed by human activities.",
    opts: { A: "vulnerable", B: "safe", C: "common", D: "harmful" },
    answer: "A"
  },
  {
    id: 18,
    q: "He is ______ to video games, which negatively affects his health as well as his academic performance at school.",
    opts: { A: "creative", B: "flexible", C: "relevant", D: "addicted" },
    answer: "D"
  },
  {
    id: 19,
    q: "School-leavers should carefully ______ their future careers based on their interests, skills, and long-term goals.",
    opts: { A: "employ", B: "abandon", C: "pursue", D: "determine" },
    answer: "D"
  },
  {
    id: 20,
    q: "In the modern workplace, employees must develop strong ______ such as communication and teamwork to succeed.",
    opts: { A: "regulations", B: "soft skills", C: "specialties", D: "beliefs" },
    answer: "B"
  },
  {
    id: 21,
    q: "Many young people want to become content creators because they are ______ about sharing ideas online.",
    opts: { A: "passionate", B: "obsolete", C: "illegal", D: "historical" },
    answer: "A"
  },
  {
    id: 22,
    q: "Employers usually ______ candidates who are hard-working, confident, and willing to learn new things.",
    opts: { A: "reject", B: "dismiss", C: "resign", D: "hire" },
    answer: "D"
  },
  {
    id: 23,
    q: "The company plans to ______ more staff this year because its business has expanded rapidly and requires additional human resources.",
    opts: { A: "employ", B: "recruit", C: "widen", D: "train" },
    answer: "B"
  },
  {
    id: 24,
    q: "Although the job is quite ______ and sometimes makes employees feel under pressure, it provides valuable experience for their future careers.",
    opts: { A: "stressful", B: "flexible", C: "convenient", D: "academic" },
    answer: "A"
  },
  {
    id: 25,
    q: "Before attending the important job interview next week, he needs to ______ his English speaking skills to communicate more confidently.",
    opts: { A: "give up", B: "take off", C: "brush up", D: "turn down" },
    answer: "C"
  },
  {
    id: 26,
    q: "In order to achieve good academic results, students should ______ on their studies and avoid being distracted by social media or entertainment activities.",
    opts: { A: "connect", B: "classify", C: "subscribe", D: "concentrate" },
    answer: "D"
  },
  {
    id: 27,
    q: "She is a ______ learner, which means she can study independently without being forced or guided by teachers all the time.",
    opts: { A: "self-confident", B: "self-reliant", C: "self-motivated", D: "dependent" },
    answer: "C"
  },
  {
    id: 28,
    q: "Online learning platforms allow students to study ______ without attending face-to-face classes.",
    opts: { A: "remotely", B: "independently", C: "flexibly", D: "regularly" },
    answer: "A"
  },
  {
    id: 29,
    q: "A positive learning ______ plays an important role in helping students overcome difficulties in their studies.",
    opts: { A: "attitude", B: "environment", C: "interest", D: "characteristic" },
    answer: "A"
  },
  {
    id: 30,
    q: "Many school-leavers are encouraged to pursue ______ education to gain practical skills for future careers.",
    opts: { A: "traditional", B: "potential", C: "proposal", D: "vocational" },
    answer: "D"
  },
  {
    id: 31,
    q: "The ______ of digital media has changed the way the press distributes information to the public worldwide.",
    opts: { A: "develop", B: "developing", C: "development", D: "developed" },
    answer: "C"
  },
  {
    id: 32,
    q: "Journalists must write articles ______ to maintain their reputation as reliable and professional reporters.",
    opts: { A: "polite", B: "politely", C: "politeness", D: "impolite" },
    answer: "B"
  },
  {
    id: 33,
    q: "Scientists must carefully ______ the data before making decisions about wildlife protection strategies.",
    opts: { A: "evaluation", B: "evaluate", C: "evaluative", D: "evaluated" },
    answer: "D"
  },
  {
    id: 34,
    q: "He is a very ______ worker who always completes tasks on time and works well with others.",
    opts: { A: "confident", B: "confidence", C: "confidently", D: "confide" },
    answer: "A"
  },
  {
    id: 35,
    q: "His strong ______ helped him overcome many obstacles and achieve success in his academic journey.",
    opts: { A: "determine", B: "determination", C: "determined", D: "determinately" },
    answer: "B"
  },
  {
    id: 36,
    q: "The company had a technician ______ the robot’s software after it made several serious mistakes during operation.",
    opts: { A: "update", B: "updated", C: "updating", D: "to update" },
    answer: "A"
  },
  {
    id: 37,
    q: "The manager got the AI system ______ by experts to ensure accurate performance in complex working environments.",
    opts: { A: "check", B: "checking", C: "checked", D: "to check" },
    answer: "C"
  },
  {
    id: 38,
    q: "AI-based robots can do household chores ______ they were humans.",
    opts: { A: "because", B: "as if", C: "although", D: "than" },
    answer: "B"
  },
  {
    id: 39,
    q: "Social media spreads information much faster ______ traditional forms of mass media like newspapers and television.",
    opts: { A: "similar to", B: "compared to", C: "more than", D: "than" },
    answer: "D"
  },
  {
    id: 40,
    q: "If people ______ cutting down forests, many animals will lose their natural habitats and may become extinct.",
    opts: { A: "continue", B: "continued", C: "will continue", D: "continuing" },
    answer: "A"
  },
  {
    id: 41,
    q: "Many endangered species will disappear ______ humans take immediate action to protect their habitats and ecosystems.",
    opts: { A: "if", B: "in case", C: "or else", D: "unless" },
    answer: "D"
  },
  {
    id: 42,
    q: "Students should ______ online resources such as e-books and educational websites to improve their learning efficiency.",
    opts: { A: "make use of", B: "run out of", C: "look up to", D: "get along with" },
    answer: "A"
  },
  {
    id: 43,
    q: "People are encouraged to ______ plastic use to protect the environment and reduce pollution.",
    opts: { A: "cut down on", B: "come up with", C: "take part in", D: "look forward to" },
    answer: "A"
  },
  {
    id: 44,
    q: "The instructor told the students ______ regularly if they wanted to improve their academic performance.",
    opts: { A: "study", B: "to study", C: "studying", D: "studied" },
    answer: "B"
  },
  {
    id: 45,
    q: "My teacher ______ me to join more extracurricular activities to develop soft skills and confidence.",
    opts: { A: "decided", B: "promised", C: "offered", D: "advised" },
    answer: "D"
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
