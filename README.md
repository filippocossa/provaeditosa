<html lang="it">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>News - Edita</title>
  <style>
    /* Stili generali */
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
      background-color: #f4f4f4;
      display: flex;
      justify-content: center;
      align-items: center;
      min-height: 100vh;
      background-color: #333;
    }
    
    /* Cornice del telefono */
    .phone-container {
      width: 414px;
      height: 896px;
      background: #111;
      border-radius: 40px;
      padding: 20px;
      box-sizing: border-box;
      position: relative;
      box-shadow: 0 0 0 4px #333, 0 0 0 8px #666, 0 20px 40px rgba(0,0,0,0.5);
    }
    
    /* Notch superiore */
    .phone-notch {
      position: absolute;
      top: 0;
      left: 50%;
      transform: translateX(-50%);
      width: 180px;
      height: 30px;
      background: #111;
      border-bottom-left-radius: 15px;
      border-bottom-right-radius: 15px;
      z-index: 10;
    }
    
    /* Container principale */
    .main-container {
      width: 100%;
      height: 100%;
      position: relative;
      background-color: white;
      overflow: hidden;
      border-radius: 20px;
    }

    /* Schermate introduttive */
    .intro-screen {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: #f4a261;
      display: flex;
      justify-content: center;
      align-items: center;
      flex-direction: column;
      text-align: center;
      padding: 20px;
      box-sizing: border-box;
      z-index: 1000;
    }

    .intro-content {
      width: 100%;
      height: 100%;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      position: relative;
    }

    .welcome-title {
      font-size: 24px;
      font-weight: bold;
      margin-bottom: 20px;
      color: white;
    }

    .welcome-subtitle {
      font-size: 18px;
      margin-bottom: 30px;
      color: white;
    }

    .welcome-box {
      background: white;
      padding: 30px;
      border-radius: 15px;
      text-align: center;
      width: 100%;
      max-width: 350px;
    }

    .intro-title {
      font-size: 22px;
      font-weight: bold;
      margin-bottom: 20px;
      color: white;
    }

    .intro-text {
      font-size: 16px;
      margin-bottom: 30px;
      color: white;
      padding: 0 20px;
    }

    /* Stile nuove frecce */
    .arrow-container {
      position: relative;
      width: 100%;
      height: 50px;
      margin: 10px 0;
    }

    .pointing-arrow {
      position: absolute;
      font-size: 40px;
      color: #FFD700;
      font-weight: bold;
      bottom: 0;
      transform: scaleY(1.5);
      text-shadow: 0 2px 4px rgba(0,0,0,0.3);
    }

    #username-input {
      width: 100%;
      padding: 10px;
      margin: 15px 0;
      border: 2px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
      text-align: center;
      max-width: 300px;
    }

    .welcome-box button, .intro-button {
      background-color: #2d86ff;
      color: white;
      border: none;
      padding: 12px 25px;
      border-radius: 20px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s;
      margin: 10px 0;
    }

    .welcome-box button:hover, .intro-button:hover {
      background-color: #1a6fd9;
    }

    /* Pulsante profilo in alto */
    .profile-button {
      position: absolute;
      top: 15px;
      right: 15px;
      background: none;
      border: none;
      font-size: 24px;
      cursor: pointer;
      z-index: 10;
      color: white;
      padding: 5px;
    }

    /* Messaggio di benvenuto */
    .welcome-message {
      position: fixed;
      top: 20px;
      left: 50%;
      transform: translateX(-50%);
      background: rgba(0,0,0,0.7);
      color: white;
      padding: 10px 20px;
      border-radius: 20px;
      z-index: 1001;
      transition: opacity 1s;
      max-width: 400px;
      width: 90%;
      box-sizing: border-box;
    }

    /* Stili esistenti */
    .container {
      width: 100%;
      max-width: 400px;
      margin: auto;
      background-color: white;
      border-radius: 10px;
      overflow: hidden;
      position: relative;
      display: none;
    }
    
    .header {
      background-color: #f4a261;
      padding: 15px;
      text-align: center;
      font-weight: bold;
      position: relative;
    }
    
    .bottom-menu {
      display: flex;
      justify-content: space-around;
      padding: 10px;
      background-color: #f4a261;
      position: fixed;
      bottom: 0;
      width: 100%;
      max-width: 400px;
      box-sizing: border-box;
    }

    .bottom-menu-placeholder {
      display: flex;
      justify-content: space-around;
      padding: 10px;
      background-color: rgba(244, 162, 97, 0.9);
      position: fixed;
      bottom: 0;
      width: 100%;
      max-width: 400px;
      box-sizing: border-box;
    }
    
    .bottom-menu button {
      border: none;
      background: none;
      cursor: pointer;
      font-size: 18px;
      color: white;
    }

    .bottom-menu-placeholder button {
      border: none;
      background: none;
      font-size: 18px;
      color: rgba(255, 255, 255, 0.7);
      cursor: default;
    }

    .active-tab {
      color: white !important;
      transform: scale(1.2);
      transition: transform 0.2s;
    }
    
    .news-item {
      padding: 15px;
      margin: 10px;
      border-radius: 10px;
      text-align: center;
      position: relative;
    }
    
    /* Rimuovi ombra dall'ultimo elemento */
    .news-list .news-item:last-child {
      box-shadow: none;
      margin-bottom: 70px; /* Spazio per il menu */
    }
    
    .filtro-box {
      display: flex;
      justify-content: center;
      padding: 10px;
      background-color: #f4a261;
      flex-wrap: wrap;
      position: relative;
    }
    
    .filtro-box button {
      padding: 8px 12px;
      border-radius: 20px;
      background-color: white;
      border: none;
      cursor: pointer;
      margin: 5px;
    }
    
    .filtro-opzioni {
      display: none;
      position: absolute;
      top: 100%;
      left: 0;
      width: 100%;
      background-color: white;
      border-radius: 0 0 10px 10px;
      z-index: 100;
      padding: 5px;
      text-align: center;
    }
    
    .filtro-opzioni button {
      margin: 4px;
      padding: 6px 10px;
      border-radius: 10px;
      border: 1px solid #aaa;
      background-color: #eee;
      cursor: pointer;
      width: 90%;
    }
    
    .filter-label {
      width: 100%;
      text-align: center;
      font-weight: bold;
      margin-bottom: 5px;
      color: white;
    }
    
    @keyframes shake {
      0% { transform: translateX(0); }
      25% { transform: translateX(-2px); }
      50% { transform: translateX(2px); }
      75% { transform: translateX(-2px); }
      100% { transform: translateX(0); }
    }
    
    .shake {
      animation: shake 0.5s infinite;
      animation-iteration-count: infinite;
    }

    /* Nuovi stili per i pulsanti */
    .answer-btn {
      background-color: #2d86ff;
      color: white;
      padding: 12px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s;
      margin: 5px;
      width: calc(50% - 10px);
      box-sizing: border-box;
    }

    .answer-btn:hover {
      background-color: #1a6fd9;
    }

    .quiz-button {
      background-color: #2d86ff;
      color: white;
      padding: 10px 20px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      cursor: pointer;
      transition: background-color 0.3s;
      margin-top: 10px;
    }

    .quiz-button:hover {
      background-color: #1a6fd9;
    }

    .timeout-message {
      color: #e74c3c;
      font-weight: bold;
      margin-bottom: 15px;
      font-size: 18px;
    }

    .answers-container {
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      margin-top: 15px;
    }

    /* Nuovi stili aggiunti */
    .logout-btn {
      background-color: #e74c3c !important;
      margin-top: 10px;
    }

    .course-btn {
      background-color: #2ecc71 !important;
      margin-top: 10px;
    }

    .retry-btn {
      background-color: #f39c12 !important;
      margin-top: 20px;
    }

    .completed-message {
      text-align: center;
      padding: 20px;
      background-color: #f8f9fa;
      border-radius: 10px;
      margin: 20px;
    }

    .retry-options {
      display: flex;
      flex-direction: column;
      gap: 10px;
      margin-top: 20px;
    }

    /* Stile per il timer */
    #timeLeft:after {
      content: "s";
      margin-left: 2px;
    }

    /* Stile per il link "Scopri di più" */
    .discover-more {
      position: absolute;
      bottom: 10px;
      right: 10px;
      color: blue;
      font-style: italic;
      text-decoration: underline;
      font-size: 14px;
      cursor: pointer;
    }

    /* Stili per il dettaglio notizia */
    .news-detail {
      display: none;
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: rgba(0,0,0,0.8);
      z-index: 1000;
      justify-content: center;
      align-items: center;
    }

    .news-content {
      width: 90%;
      max-width: 400px;
      border-radius: 10px;
      padding: 20px;
      box-sizing: border-box;
      position: relative;
    }

    .news-title {
      font-size: 20px;
      font-weight: bold;
      margin-bottom: 15px;
      text-align: center;
    }

    .news-image-placeholder {
      height: 150px;
      background-color: rgba(255,255,255,0.2);
      display: flex;
      justify-content: center;
      align-items: center;
      margin-bottom: 15px;
      border-radius: 5px;
    }

    .news-text {
      margin-bottom: 20px;
      line-height: 1.5;
    }

    .news-buttons {
      display: flex;
      flex-direction: column;
      gap: 10px;
    }

    .news-button {
      padding: 10px;
      border: none;
      border-radius: 5px;
      background-color: #2d86ff;
      color: white;
      cursor: pointer;
      text-align: center;
    }

    .close-button {
      position: absolute;
      top: 10px;
      right: 10px;
      background: none;
      border: none;
      color: white;
      font-size: 20px;
      cursor: pointer;
    }
  </style>
</head>
<body>
  <div class="phone-container">
    <div class="phone-notch"></div>
    <div class="main-container">
      <!-- Schermata iniziale -->
      <div id="initial-screen" class="intro-screen">
        <div class="intro-content">
          <h1 class="welcome-title">Sei pronto a scoprire l'attualità divertendoti e ad avere un impatto sul mondo che ti circonda?</h1>
          <p class="welcome-subtitle">Benvenuto su EditAPP</p>
          <button id="start-intro" class="intro-button">INIZIAMO</button>
          
          <!-- Menu placeholder -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <!-- Schermata di benvenuto con nome -->
      <div id="welcome-screen" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <div class="welcome-box">
            <h2>Come ti chiami?</h2>
            <input type="text" id="username-input" placeholder="Il tuo nome" maxlength="20">
            <button id="name-submit">CONTINUA</button>
          </div>
          
          <!-- Menu placeholder -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <!-- Schermate introduttive -->
      <div id="intro-screen-1" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Ma come funziona EditAPP?</h2>
          <button id="discover-button" class="intro-button">Scopriamolo insieme</button>
          
          <!-- Menu placeholder -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <div id="intro-screen-2" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Sezione NEWS</h2>
          <p class="intro-text">Ti sei perso le notizie dell'ultima ora o a fine giornata vuoi sapere cos'è successo nel mondo? Nella sezione "NEWS" puoi trovare tutte le notizie riassunte in breve e poi approfondire quelle che ti interessano maggiormente.</p>
          
          <button id="proceed-button-1" class="intro-button">PROCEDIAMO</button>
          
          <div class="arrow-container">
            <div class="pointing-arrow" style="left: 12%">↓</div>
          </div>
          
          <!-- Menu placeholder con icona NEWS evidenziata -->
          <div class="bottom-menu-placeholder">
            <button class="active-tab">📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <div id="intro-screen-3" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Sezione GAME</h2>
          <p class="intro-text">Vuoi metterti alla prova per essere sicuro di aver capito cosa sta succedendo nel mondo tramite giochi e quiz? Nella sezione "GAME" puoi trovare tutti i giochi e sfidare i tuoi amici a fare meglio di te.</p>
          
          <button id="proceed-button-2" class="intro-button">PROCEDIAMO</button>
          
          <div class="arrow-container">
            <div class="pointing-arrow" style="left: 37%">↓</div>
          </div>
          
          <!-- Menu placeholder con icona GAME evidenziata -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button class="active-tab">🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <div id="intro-screen-4" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Sezione EDU</h2>
          <p class="intro-text">Vuoi imparare in poco tempo cos'è successo in una determinata parte del mondo e perché OGGI sta succedendo qualcosa? Nella sezione "EDU" puoi trovare tantissimi percorsi che ti aiuteranno a farlo, in pochissimo tempo e divertendoti.</p>
          
          <button id="proceed-button-3" class="intro-button">PROCEDIAMO</button>
          
          <div class="arrow-container">
            <div class="pointing-arrow" style="left: 62%">↓</div>
          </div>
          
          <!-- Menu placeholder con icona EDU evidenziata -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button class="active-tab">🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <div id="intro-screen-5" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Sezione DICCI LA TUA</h2>
          <p class="intro-text">Finalmente senti di avere le basi per cambiare il mondo? Nella sezione "DICCI LA TUA" puoi aiutarci a raccogliere le opinioni della nostra generazione e firmare/proporre petizioni che rispecchino i tuoi interessi!</p>
          
          <button id="proceed-button-4" class="intro-button">PROCEDIAMO</button>
          
          <div class="arrow-container">
            <div class="pointing-arrow" style="left: 87%">↓</div>
          </div>
          
          <!-- Menu placeholder con icona DICCI LA TUA evidenziata -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button class="active-tab">📋</button>
          </div>
        </div>
      </div>

      <!-- Nuova schermata finale -->
      <div id="intro-screen-6" class="intro-screen" style="display: none;">
        <div class="intro-content">
          <h2 class="intro-title">Sei pronto ad iniziare?</h2>
          <p class="intro-text">Ora hai tutte le informazioni per usare al meglio EditAPP. Clicca il pulsante qui sotto per iniziare la tua esperienza!</p>
          
          <button id="final-start-button" class="intro-button">ANDIAMO</button>
          
          <!-- Menu placeholder -->
          <div class="bottom-menu-placeholder">
            <button>📰</button>
            <button>🎮</button>
            <button>🎓</button>
            <button>📋</button>
          </div>
        </div>
      </div>

      <!-- App principale (nascosta inizialmente) -->
      <div id="app-container" class="container"></div>

      <!-- Dettaglio notizia (nascosto inizialmente) -->
      <div class="news-detail" id="newsDetail"></div>

      <!-- Pulsante profilo fisso in alto a destra -->
      <button id="profile-button" class="profile-button" style="display: none;">👤</button>
    </div>
  </div>

  <script>
    // Variabili globali
    let currentUser = null;
    let puntiCorretti = 0;
    let punteggioTotale = 0;
    let daziInterval = null;
    let currentQuestionIndex = 0;
    let completedGame = false;
    let wrongAnswers = [];
    let isRetryMode = false;
    let timedOutQuestions = [];

    // Domande del quiz
    const quizQuestions = [
      {
        testo: "Se oggi una friggitrice ad aria, tipicamente venduta da una compagnia americana, costa 150€, quanto potrebbe costare con l'introduzione dei dazi?",
        opzioni: ["225€", "125€", "150€", "200€"],
        corretta: "A",
        difficolta: "media",
        punti: 200,
        difficultyMultiplier: 1.2
      },
      {
        testo: "Domanda 2: Quanto aumentano generalmente i prezzi con dazi del 25%?",
        opzioni: ["10-15%", "20-25%", "25-30%", "35-40%"],
        corretta: "B",
        difficolta: "media",
        punti: 200,
        difficultyMultiplier: 1.2
      },
      {
        testo: "Domanda 3: Qual è l'impatto principale dei dazi sui consumatori?",
        opzioni: ["Più scelta", "Prezzi più bassi", "Prezzi più alti", "Nessun cambiamento"],
        corretta: "C",
        difficolta: "media",
        punti: 200,
        difficultyMultiplier: 1.2
      },
      {
        testo: "Domanda 4: Quale settore è più protetto dai dazi UE?",
        opzioni: ["Tecnologia", "Automotive", "Agricoltura", "Tessile"],
        corretta: "C",
        difficolta: "difficile",
        punti: 300,
        difficultyMultiplier: 1.5
      },
      {
        testo: "Domanda 5: Quanti dazi ha introdotto l'UE nel 2023?",
        opzioni: ["5", "12", "18", "23"],
        corretta: "D",
        difficolta: "difficile",
        punti: 300,
        difficultyMultiplier: 1.5
      }
    ];

    // Notizie con contenuti (modificate come richiesto)
    const newsItems = [
      { 
        titolo: "ITALIA - Meloni: L'Europa di Ventotene non è la mia", 
        tema: "Italia", 
        colore: "gray", 
        testoColore: "white",
        contenuto: "Durante un recente discorso, la Presidente del Consiglio Giorgia Meloni ha espresso la sua visione alternativa dell'Europa, distanziandosi dal modello federalista nato dal Manifesto di Ventotene. Secondo Meloni, l'UE dovrebbe essere un'alleanza di nazioni sovrane piuttosto che un super-stato centralizzato. La posizione ha suscitato reazioni contrastanti nel panorama politico europeo."
      },
      { 
        titolo: "MONDO - Donald Trump firma i dazi contro l'UE", 
        tema: "Mondo", 
        colore: "red", 
        testoColore: "white",
        contenuto: "Il presidente americano Donald Trump ha firmato una nuova serie di dazi commerciali contro i prodotti europei, in particolare nel settore automobilistico e aeronautico. Questa mossa rischia di inasprire ulteriormente le relazioni transatlantiche e potrebbe avere ripercussioni sull'economia globale."
      },
      { 
        titolo: "EUROPA - Ursula Von Der Leyen: I dazi americani non ci spaventano", 
        tema: "Europa", 
        colore: "cornflowerblue", 
        testoColore: "white",
        contenuto: "La Presidente della Commissione Europea Ursula Von Der Leyen ha dichiarato che l'UE è pronta a rispondere ai nuovi dazi americani con misure proporzionate. \"Abbiamo strumenti per difendere il nostro mercato e i nostri cittadini\", ha affermato durante una conferenza stampa a Bruxelles."
      },
      { 
        titolo: "ECONOMIA - La BCE taglia i tassi di interesse", 
        tema: "Economia", 
        colore: "green", 
        testoColore: "white",
        contenuto: "La Banca Centrale Europea ha annunciato un taglio dei tassi di interesse dello 0,25% nel tentativo di stimolare la crescita economica nella zona euro. La mossa è stata interpretata come una risposta al rallentamento economico globale e alle tensioni commerciali."
      }
    ];

    // [RESTANTE PARTE DEL CODICE JAVASCRIPT RIMANE INVARIATA...]
    // ... (inserire qui tutto il resto del codice JavaScript dalla versione precedente)
    
    // Funzioni di navigazione
    function showNews(filter = null) {
      clearIntervals();
      
      let news = [...newsItems]; // Copia l'array delle notizie

      if (filter) {
        news = news.filter(n => n.tema.toLowerCase() === filter.toLowerCase());
      }

      let newsHTML = news.map(n => `
        <div class='news-item' style='background-color: ${n.colore}; color: ${n.testoColore};'>
          <strong>${n.titolo}</strong>
          <div class="discover-more" data-titolo="${n.titolo}" data-contenuto="${n.contenuto}" data-colore="${n.colore}" data-testocolore="${n.testoColore}" data-tema="${n.tema}">Scopri di più</div>
        </div>`).join("");

      document.getElementById('app-container').innerHTML = `
        <div class="header">
          Le notizie dell'ultima ora
        </div>
        <div class='filtro-box'>
          <div class='filter-label'>Filtra per</div>
          <button id="filter-toggle" class="news-filter">Tematica</button>
          <div id="filtro-opzioni" class="filtro-opzioni">
            <button class="news-filter" data-filter="all">Tutte</button>
            <button class="news-filter" data-filter="Italia">Italia</button>
            <button class="news-filter" data-filter="Mondo">Mondo</button>
            <button class="news-filter" data-filter="Europa">Europa</button>
            <button class="news-filter" data-filter="Economia">Economia</button>
          </div>
        </div>
        <div class="news-list">
          ${newsHTML}
        </div>
        ${getBottomMenu('news')}`;

      // Aggiungi event listener per i filtri
      document.getElementById('filter-toggle').addEventListener('click', function() {
        const filtroBox = document.getElementById("filtro-opzioni");
        filtroBox.style.display = (filtroBox.style.display === "block") ? "none" : "block";
      });

      document.querySelectorAll('.news-filter[data-filter]').forEach(button => {
        button.addEventListener('click', function() {
          const filter = this.dataset.filter;
          showNews(filter === 'all' ? null : filter);
          document.getElementById("filtro-opzioni").style.display = "none";
        });
      });

      // Aggiungi event listener per i dettagli delle notizie
      document.querySelectorAll('.discover-more').forEach(item => {
        item.addEventListener('click', function(e) {
          e.stopPropagation();
          showNewsDetail(
            this.getAttribute('data-titolo'),
            this.getAttribute('data-contenuto'),
            this.getAttribute('data-colore'),
            this.getAttribute('data-testocolore'),
            this.getAttribute('data-tema')
          );
        });
      });
    }

    function showNewsDetail(titolo, contenuto, colore, testoColore, tema) {
      let buttonsHTML = '';
      
      // Personalizza i pulsanti in base al tema della notizia
      switch(tema) {
        case 'Italia':
          buttonsHTML = `
            <button class="news-button" id="ventoteneButton">Scopri perché Ventotene è importante per la storia europea</button>
            <button class="news-button" id="europaNewsButton">Altre notizie sull'Europa</button>
          `;
          break;
        case 'Mondo':
          buttonsHTML = `
            <button class="news-button" id="daziGameButton">Quale sarà l'effetto dei dazi sulle nostre vite?</button>
            <button class="news-button" id="mondoNewsButton">Altre notizie dal Mondo</button>
          `;
          break;
        case 'Europa':
          buttonsHTML = `
            <button class="news-button" id="europaNewsButton">Altre notizie sull'Europa</button>
          `;
          break;
        case 'Economia':
          buttonsHTML = `
            <button class="news-button" id="tassiButton">Come funzionano i tassi di interesse?</button>
            <button class="news-button" id="economiaNewsButton">Altre notizie sull'economia</button>
          `;
          break;
        default:
          buttonsHTML = `
            <button class="news-button" id="defaultButton">Scopri di più</button>
          `;
      }

      const detailHTML = `
        <div class="news-content" style="background-color: ${colore}; color: ${testoColore}">
          <button class="close-button">×</button>
          <div class="news-title">${titolo}</div>
          <div class="news-image-placeholder">[Spazio per immagine]</div>
          <div class="news-text">${contenuto}</div>
          <div class="news-buttons">
            ${buttonsHTML}
          </div>
        </div>`;
      
      document.getElementById('newsDetail').innerHTML = detailHTML;
      document.getElementById('newsDetail').style.display = 'flex';
      
      // Chiudi il dettaglio
      document.querySelector('.close-button').addEventListener('click', function() {
        document.getElementById('newsDetail').style.display = 'none';
      });
      
      // Chiudi cliccando fuori dal contenuto
      document.getElementById('newsDetail').addEventListener('click', function(e) {
        if(e.target === this) {
          this.style.display = 'none';
        }
      });
      
      // Gestione dei pulsanti in base al tema
      if (document.getElementById('ventoteneButton')) {
        document.getElementById('ventoteneButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          showEdu();
        });
      }
      
      if (document.getElementById('europaNewsButton')) {
        document.getElementById('europaNewsButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          showNews('Europa');
        });
      }
      
      if (document.getElementById('daziGameButton')) {
        document.getElementById('daziGameButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          startDaziGame();
        });
      }
      
      if (document.getElementById('mondoNewsButton')) {
        document.getElementById('mondoNewsButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          showNews('Mondo');
        });
      }
      
      if (document.getElementById('tassiButton')) {
        document.getElementById('tassiButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          showEdu('Economia');
        });
      }
      
      if (document.getElementById('economiaNewsButton')) {
        document.getElementById('economiaNewsButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
          showNews('Economia');
        });
      }
      
      if (document.getElementById('defaultButton')) {
        document.getElementById('defaultButton').addEventListener('click', function() {
          document.getElementById('newsDetail').style.display = 'none';
        });
      }
    }

    function showGame() {
      clearIntervals();
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          Mettiti alla prova
        </div>
        <div class='news-list'>
          <div class='news-item' style='background-color: #3498db; color: white;'>
            <strong>QUIZ DEL GIORNO</strong>
            <p>L'Unione Europea ha annunciato di volersi riarmare, è davvero così e soprattutto può?</p>
            <button class="quiz-button">Verifica quante ne sai</button>
          </div>
          <div class='news-item' style='background-color: #8e44ad; color: white;'>
            <strong>UN SEMPREVERDE</strong>
            <p>Le politiche di Milei in Argentina non sembrano cambiare l'economia e l'inflazione galoppa</p>
            <button class="quiz-button">Gioca a "Quanto costerà domani"</button>
          </div>
          <div class='news-item' style='background-color: #e74c3c; color: white;'>
            <strong>POTREBBE INTERESSARTI</strong>
            <p>I dazi imposti dall'Unione Europea avranno un impatto tangibile sulle nostre vite, ma lo conosci davvero?</p>
            <button id="start-dazi-game" class="quiz-button">Verificalo qui</button>
          </div>
        </div>
        ${getBottomMenu('game')}`;
        
      document.getElementById('start-dazi-game').addEventListener('click', startDaziGame);
    }

    function showEdu(filter = null) {
      clearIntervals();
      
      let courses = [
        { titolo: "LA LEGGE DI BILANCIO IN ITALIA - ITALIA", tema: "Italia", colore: "gray", testoColore: "white" },
        { titolo: "LA SITUAZIONE IN MEDIO ORIENTE - GEOPOLITICA", tema: "Geopolitica", colore: "red", testoColore: "white" },
        { titolo: "LA STORIA DELL'UNIONE EUROPEA - EUROPA", tema: "Europa", colore: "cornflowerblue", testoColore: "white" },
        { titolo: "I TASSI DI INTERESSE - ECONOMIA", tema: "Economia", colore: "green", testoColore: "white" }
      ];

      if (filter) {
        courses = courses.filter(c => c.tema.toLowerCase() === filter.toLowerCase());
      }

      let coursesHTML = courses.map(c => `
        <div class='news-item' style='background-color: ${c.colore}; color: ${c.testoColore};'>
          <strong>${c.titolo}</strong>
        </div>`).join("");

      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          RIPARTIAMO DALLA PRIMA PUNTATA
        </div>
        <div class='filtro-box'>
          <div class='filter-label'>Filtra per</div>
          <button id="edu-filter-toggle" class="edu-filter">Tematica</button>
          <div id="edu-filtro-opzioni" class="filtro-opzioni">
            <button class="edu-filter" data-filter="all">Tutti</button>
            <button class="edu-filter" data-filter="Italia">Italia</button>
            <button class="edu-filter" data-filter="Geopolitica">Geopolitica</button>
            <button class="edu-filter" data-filter="Europa">Europa</button>
            <button class="edu-filter" data-filter="Economia">Economia</button>
          </div>
        </div>
        <div class='news-list'>
          ${coursesHTML}
        </div>
        ${getBottomMenu('edu')}`;

      // Aggiungi event listener per i filtri
      document.getElementById('edu-filter-toggle').addEventListener('click', function() {
        const filtroBox = document.getElementById("edu-filtro-opzioni");
        filtroBox.style.display = (filtroBox.style.display === "block") ? "none" : "block";
      });

      document.querySelectorAll('.edu-filter[data-filter]').forEach(button => {
        button.addEventListener('click', function() {
          const filter = this.dataset.filter;
          showEdu(filter === 'all' ? null : filter);
          document.getElementById("edu-filtro-opzioni").style.display = "none";
        });
      });
    }

    function showParticipate(filtro = null) {
      clearIntervals();
      
      let news = [
        { titolo: "IL VOTO FUORISEDE", area: "Nazionale", colore: "#cccccc", testoColore: "black" },
        { titolo: "LA NUOVA LINEA DELLA METROPOLITANA", area: "Locale", colore: "#e74c3c", testoColore: "white" },
        { titolo: "LA RISPOSTA EUROPEA AI DAZI AMERICANI", area: "Globale", colore: "#3498db", testoColore: "white" }
      ];

      if (filtro) {
        news = news.filter(n => n.area.toLowerCase() === filtro.toLowerCase());
      }

      let newsHTML = news.map(n => `
        <div class='news-item' style='background-color: ${n.colore}; color: ${n.testoColore};'>
          <strong>${n.titolo}</strong><br><em>${n.area.toUpperCase()}</em>
        </div>`).join("");

      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          DICCI LA TUA
        </div>
        <div class='filtro-box'>
          <div class='filter-label'>Filtra per</div>
          <button id="part-filter-toggle" class="filter-option">Area</button>
          <div id="part-filtro-opzioni" class="filtro-opzioni">
            <button class="filter-option" data-area="all">Tutti</button>
            <button class="filter-option" data-area="Nazionale">Nazionale</button>
            <button class="filter-option" data-area="Locale">Locale</button>
            <button class="filter-option" data-area="Globale">Globale</button>
          </div>
        </div>
        <div class='news-list'>
          ${newsHTML}
        </div>
        ${getBottomMenu('participate')}`;

      // Aggiungi event listener per i filtri
      document.getElementById('part-filter-toggle').addEventListener('click', function() {
        const filtroBox = document.getElementById("part-filtro-opzioni");
        filtroBox.style.display = (filtroBox.style.display === "block") ? "none" : "block";
      });

      document.querySelectorAll('.filter-option[data-area]').forEach(button => {
        button.addEventListener('click', function() {
          const area = button.dataset.area;
          showParticipate(area === 'all' ? null : area);
          document.getElementById("part-filtro-opzioni").style.display = "none";
        });
      });
    }

    function showProfile() {
      clearIntervals();
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          Il tuo profilo
        </div>
        <div style='padding: 20px;'>
          <h3>Ciao ${currentUser}!</h3>
          <p>Punteggio totale: ${punteggioTotale} punti</p>
          <p>Risposte corrette: ${puntiCorretti}/${quizQuestions.length}</p>
          <button id="reset-progress" class="quiz-button" style="background-color: #e74c3c;">Azzera progressi</button>
          <button id="logout-btn" class="quiz-button logout-btn">Esci e cambia account</button>
        </div>
        ${getBottomMenu()}`;
        
      document.getElementById('reset-progress').addEventListener('click', resetProgress);
      document.getElementById('logout-btn').addEventListener('click', logout);
    }

    function logout() {
      if(confirm("Vuoi davvero uscire e cambiare account?")) {
        localStorage.removeItem('edita_username');
        localStorage.removeItem(`edita_progress_${currentUser}`);
        localStorage.removeItem(`edita_completed_${currentUser}`);
        location.reload();
      }
    }

    // Funzioni di utilità
    function getBottomMenu(activeTab = null) {
      let newsBtn = '📰';
      let gameBtn = '🎮';
      let eduBtn = '🎓';
      let partBtn = '📋';
      
      if (activeTab === 'news') newsBtn = '<span class="active-tab">📰</span>';
      if (activeTab === 'game') gameBtn = '<span class="active-tab">🎮</span>';
      if (activeTab === 'edu') eduBtn = '<span class="active-tab">🎓</span>';
      if (activeTab === 'participate') partBtn = '<span class="active-tab">📋</span>';
      
      return `
      <div class='bottom-menu'>
        <button id="btn-news">${newsBtn}</button>
        <button id="btn-game">${gameBtn}</button>
        <button id="btn-edu">${eduBtn}</button>
        <button id="btn-part">${partBtn}</button>
      </div>`;
    }

    function clearIntervals() {
      if(daziInterval) {
        clearInterval(daziInterval);
        daziInterval = null;
      }
    }

    // Funzioni per la gestione dell'utente
    function startApp() {
      const username = document.getElementById('username-input').value.trim();
      if(username === '') {
        alert("Per favore inserisci un nome!");
        return;
      }
      
      currentUser = username;
      localStorage.setItem('edita_username', username);
      
      document.getElementById('welcome-screen').style.display = 'none';
      document.getElementById('intro-screen-1').style.display = 'flex';
    }

    function showWelcomeMessage() {
      const welcomeMsg = document.createElement('div');
      welcomeMsg.className = 'welcome-message';
      welcomeMsg.innerHTML = `👋 Benvenuto <strong>${currentUser}</strong>!`;
      document.body.appendChild(welcomeMsg);
      
      setTimeout(() => {
        welcomeMsg.style.opacity = '0';
        setTimeout(() => welcomeMsg.remove(), 1000);
      }, 3000);
    }

    // Funzioni per il salvataggio dei progressi
    function saveProgress() {
      if(!currentUser) return;
      
      const progressData = {
        username: currentUser,
        lastPlayed: new Date().toISOString(),
        score: punteggioTotale,
        correctAnswers: puntiCorretti,
        wrongAnswers: wrongAnswers,
        timedOutQuestions: timedOutQuestions
      };
      
      localStorage.setItem(`edita_progress_${currentUser}`, JSON.stringify(progressData));
    }

    function loadProgress() {
      if(!currentUser) return;
      
      const savedData = localStorage.getItem(`edita_progress_${currentUser}`);
      if(savedData) {
        const progress = JSON.parse(savedData);
        punteggioTotale = progress.score || 0;
        puntiCorretti = progress.correctAnswers || 0;
        wrongAnswers = progress.wrongAnswers || [];
        timedOutQuestions = progress.timedOutQuestions || [];
      }
    }

    function resetProgress() {
      if(confirm("Sicuro di voler azzerare tutti i progressi?")) {
        punteggioTotale = 0;
        puntiCorretti = 0;
        wrongAnswers = [];
        timedOutQuestions = [];
        completedGame = false;
        localStorage.removeItem(`edita_completed_${currentUser}`);
        saveProgress();
        showProfile();
      }
    }

    // Funzioni del gioco
    function startDaziGame() {
      loadProgress();
      
      // Controlla se il gioco è già stato completato
      const gameCompleted = localStorage.getItem(`edita_completed_${currentUser}`);
      if(gameCompleted) {
        showRetryScreen();
        return;
      }
      
      // Altrimenti inizia un nuovo gioco
      puntiCorretti = 0;
      currentQuestionIndex = 0;
      wrongAnswers = [];
      timedOutQuestions = [];
      isRetryMode = false;
      showQuestion(currentQuestionIndex);
    }

    function showRetryScreen() {
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          Già completato!
        </div>
        <div class='completed-message'>
          <h3>Hai già completato questo gioco!</h3>
          <p>Vuoi correggere gli errori?</p>
          <div class="retry-options">
            <button id="retry-yes" class="quiz-button retry-btn">Sì, correggi errori</button>
            <button id="retry-no" class="quiz-button">No, torna ai giochi</button>
          </div>
        </div>
        ${getBottomMenu('game')}`;
        
      document.getElementById('retry-yes').addEventListener('click', () => {
        isRetryMode = true;
        currentQuestionIndex = 0;
        
        // Uniamo domande sbagliate e a tempo scaduto
        const allQuestionsToRetry = [...wrongAnswers, ...timedOutQuestions];
        // Rimuoviamo duplicati
        wrongAnswers = [...new Set(allQuestionsToRetry)];
        
        showRetryQuestions();
      });
      
      document.getElementById('retry-no').addEventListener('click', showGame);
    }

    function showRetryQuestions() {
      if(wrongAnswers.length === 0) {
        showResults(true);
        return;
      }

      showNextRetryQuestion();
    }

    function showNextRetryQuestion() {
      if(currentQuestionIndex >= wrongAnswers.length) {
        showResults(true);
        return;
      }

      const originalQuestionIndex = quizQuestions.findIndex(q => q.testo === wrongAnswers[currentQuestionIndex].testo);
      const question = quizQuestions[originalQuestionIndex];
      
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          CORREGGI GLI ERRORI (${currentQuestionIndex + 1}/${wrongAnswers.length})
        </div>
        <div style='background-color: #d66ef1; padding: 20px; height: calc(100vh - 120px); box-sizing: border-box;'>
          <div>
            <div style='text-align: center; font-weight: bold; margin-bottom: 5px;'>Time left: <span id="timeLeft">10</span></div>
            <div id="progressContainer" style="background-color: #ccc; border-radius: 20px; height: 20px; width: 100%; margin-bottom: 20px;">
              <div id="progressBar" style="background-color: #2d86ff; height: 100%; width: 100%; border-radius: 20px;"></div>
            </div>
            <p style='text-align: center; font-size: 14px; font-weight: bold;'>Difficoltà: ${question.difficolta.toUpperCase()}</p>
            <p style='text-align: center; font-size: 16px; font-weight: bold;'>${question.testo}</p>
          </div>
          <div class="answers-container">
            ${question.opzioni.map((op, i) => 
              `<button class="answer-btn" data-answer="${String.fromCharCode(65 + i)}">${op}</button>`
            ).join('')}
          </div>
        </div>
        ${getBottomMenu('game')}`;

      document.querySelectorAll('.answer-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          checkAnswer(this.dataset.answer, question, true);
        });
      });

      startTimer(question, true);
    }

    function showQuestion(index) {
      if(index >= quizQuestions.length) {
        localStorage.setItem(`edita_completed_${currentUser}`, 'true');
        completedGame = true;
        showResults();
        return;
      }

      const question = quizQuestions[index];
      const questionNumber = index + 1;
      
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          L'EFFETTO DEI DAZI
        </div>
        <div style='background-color: #d66ef1; padding: 20px; height: calc(100vh - 120px); box-sizing: border-box;'>
          <div>
            <div style='text-align: center; font-weight: bold; margin-bottom: 5px;'>Time left: <span id="timeLeft">10</span></div>
            <div id="progressContainer" style="background-color: #ccc; border-radius: 20px; height: 20px; width: 100%; margin-bottom: 20px;">
              <div id="progressBar" style="background-color: #2d86ff; height: 100%; width: 100%; border-radius: 20px;"></div>
            </div>
            <p style='text-align: center; font-size: 14px; font-weight: bold;'>Domanda ${questionNumber}/${quizQuestions.length} - Difficoltà: ${question.difficolta.toUpperCase()}</p>
            <p style='text-align: center; font-size: 16px; font-weight: bold;'>${question.testo}</p>
          </div>
          <div class="answers-container">
            ${question.opzioni.map((op, i) => 
              `<button class="answer-btn" data-answer="${String.fromCharCode(65 + i)}">${op}</button>`
            ).join('')}
          </div>
        </div>
        ${getBottomMenu('game')}`;

      document.querySelectorAll('.answer-btn').forEach(btn => {
        btn.addEventListener('click', function() {
          checkAnswer(this.dataset.answer, question);
        });
      });

      startTimer(question);
    }

    function startTimer(question, isRetry = false) {
      let time = 10;
      clearIntervals();
      
      updateTimerDisplay(time);
      
      daziInterval = setInterval(() => {
        time--;
        updateTimerDisplay(time);
        
        if (time <= 0) {
          clearInterval(daziInterval);
          handleTimeout(question, isRetry);
        }
      }, 1000);
    }

    function updateTimerDisplay(time) {
      const timeDisplay = document.getElementById("timeLeft");
      const progressBar = document.getElementById("progressBar");
      if (timeDisplay) {
        timeDisplay.textContent = time;
      }
      if (progressBar) {
        const percentage = time * 10;
        progressBar.style.width = percentage + "%";
        progressBar.style.transition = `width ${time === 10 ? '0s' : '1s'} linear`;
        
        if (time > 5) {
          progressBar.style.backgroundColor = "#2ecc71";
        } else if (time > 2) {
          progressBar.style.backgroundColor = "#f39c12";
        } else {
          progressBar.style.backgroundColor = "#e74c3c";
          progressBar.classList.add("shake");
        }
      }
    }

    function handleTimeout(question, isRetry = false) {
      if(!isRetry && !isRetryMode) {
        timedOutQuestions.push(question);
      }
      showTimeoutFeedback(question, isRetry || isRetryMode);
    }

    function showTimeoutFeedback(question, isRetry = false) {
      const correctAnswer = question.opzioni[question.corretta.charCodeAt(0) - 65];
      
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          L'EFFETTO DEI DAZI
        </div>
        <div style='background-color: #d66ef1; padding: 20px; min-height: calc(100vh - 120px); box-sizing: border-box;'>
          <div style='text-align: center; margin-bottom: 20px;'>
            <div class="timeout-message">⏳ Tempo scaduto!</div>
            <div style='background-color: lightgray; padding: 15px; margin: 10px; border-radius: 20px;'>
              <strong>SPIEGAZIONE VIDEO</strong>
              <div style="height: 100px; background-color: #eee; border-radius: 10px; display: flex; align-items: center; justify-content: center;">
                [📹 spazio video in arrivo]
              </div>
              <p style="margin-top: 10px;">La risposta corretta era: <strong>${correctAnswer}</strong></p>
            </div>
            <button id="next-question-btn" class="quiz-button">${isRetry ? 'CONTINUA' : 'PROSSIMA DOMANDA'}</button>
          </div>
        </div>
        ${getBottomMenu('game')}`;
        
      document.getElementById('next-question-btn').addEventListener('click', () => {
        currentQuestionIndex++;
        if(isRetry || isRetryMode) {
          showNextRetryQuestion();
        } else {
          showQuestion(currentQuestionIndex);
        }
      });
    }

    function checkAnswer(selectedAnswer, question, isRetry = false) {
      clearInterval(daziInterval);
      const isCorrect = selectedAnswer === question.corretta;
      const timeLeft = parseInt(document.getElementById("timeLeft").textContent);
      
      let puntiAssegnati = 0;
      
      if (isCorrect) {
        // Nuovo sistema di punteggio: [(tempo rimasto/10s)*difficoltà]/2
        puntiAssegnati = Math.floor(((timeLeft / 10) * question.difficultyMultiplier) / 2 * question.punti);
        
        puntiCorretti++;
        if(isRetry || isRetryMode) {
          punteggioTotale += Math.floor(puntiAssegnati / 2);
          wrongAnswers = wrongAnswers.filter(q => q.testo !== question.testo);
          timedOutQuestions = timedOutQuestions.filter(q => q.testo !== question.testo);
        } else {
          punteggioTotale += puntiAssegnati;
        }
      } else if(!isRetry && !isRetryMode) {
        wrongAnswers.push(question);
      }
      
      saveProgress();
      showAnswerFeedback(isCorrect, question, puntiAssegnati, isRetry || isRetryMode);
    }

    function showAnswerFeedback(isCorrect, question, puntiAssegnati, isRetry = false) {
      const correctAnswer = question.opzioni[question.corretta.charCodeAt(0) - 65];
      
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          L'EFFETTO DEI DAZI
        </div>
        <div style='background-color: #d66ef1; padding: 20px; min-height: calc(100vh - 120px); box-sizing: border-box;'>
          <div style='text-align: center; margin-bottom: 20px;'>
            ${isCorrect ? 
              `<h3 style='color: green;'>✅ Risposta esatta! (+${puntiAssegnati}${isRetry ? ' (metà punti)' : ''} p)</h3>` : 
              `<h3 style='color: red;'>❌ Risposta sbagliata!</h3>
               <p>La risposta corretta era: <strong>${correctAnswer}</strong></p>`
            }
            <div style='background-color: lightgray; padding: 15px; margin: 10px; border-radius: 20px;'>
              <strong>SPIEGAZIONE VIDEO</strong>
              <div style="height: 100px; background-color: #eee; border-radius: 10px; display: flex; align-items: center; justify-content: center;">
                [📹 spazio video in arrivo]
              </div>
            </div>
            <button id="next-question-btn" class="quiz-button">${isRetry ? 'CONTINUA' : 'PROSSIMA DOMANDA'}</button>
          </div>
        </div>
        ${getBottomMenu('game')}`;
        
      document.getElementById('next-question-btn').addEventListener('click', () => {
        currentQuestionIndex++;
        if(isRetry) {
          showNextRetryQuestion();
        } else {
          showQuestion(currentQuestionIndex);
        }
      });
    }

    function showResults(isRetry = false) {
      saveProgress();
      
      let resultMessage = '';
      if(isRetry) {
        const erroriRimasti = wrongAnswers.length + timedOutQuestions.length;
        if(erroriRimasti === 0) {
          resultMessage = '<h2>Complimenti! Hai corretto tutti gli errori! 🎉</h2>';
        } else {
          const erroriCorretti = quizQuestions.length - erroriRimasti;
          resultMessage = `<h2>Hai corretto ${erroriCorretti} ${erroriCorretti === 1 ? 'errore' : 'errori'} su ${erroriCorretti + erroriRimasti}</h2>`;
        }
      } else {
        resultMessage = `<h2>Hai risposto correttamente a ${puntiCorretti} su ${quizQuestions.length} domande!</h2>`;
      }
      
      document.getElementById('app-container').innerHTML = `
        <div class='header'>
          RISULTATI FINALI
        </div>
        <div style='padding: 20px; text-align: center;'>
          ${resultMessage}
          <h3>Punteggio totale: ${punteggioTotale} punti</h3>
          <p>${isRetry ? 'Hai guadagnato metà punti per le risposte corrette!' : 'Ottimo lavoro! 💪'}</p>
          <button id="back-to-games" class="quiz-button">Torna ai giochi</button>
          <button id="course-btn" class="quiz-button course-btn">Prova un nostro corso sull'economia</button>
        </div>
        ${getBottomMenu('game')}`;
          
      document.getElementById('back-to-games').addEventListener('click', showGame);
      document.getElementById('course-btn').addEventListener('click', function() {
        showEdu();
      });
    }

    // Setup iniziale
    function setupEventListeners() {
      // Schermata iniziale
      document.getElementById('start-intro').addEventListener('click', function() {
        document.getElementById('initial-screen').style.display = 'none';
        document.getElementById('welcome-screen').style.display = 'flex';
      });

      // Schermata nome utente
      document.getElementById('name-submit').addEventListener('click', function() {
        const username = document.getElementById('username-input').value.trim();
        if(username === '') {
          alert("Per favore inserisci un nome!");
          return;
        }
        
        currentUser = username;
        localStorage.setItem('edita_username', username);
        
        document.getElementById('welcome-screen').style.display = 'none';
        document.getElementById('intro-screen-1').style.display = 'flex';
      });

      // Schermate introduttive
      document.getElementById('discover-button').addEventListener('click', function() {
        document.getElementById('intro-screen-1').style.display = 'none';
        document.getElementById('intro-screen-2').style.display = 'flex';
      });

      document.getElementById('proceed-button-1').addEventListener('click', function() {
        document.getElementById('intro-screen-2').style.display = 'none';
        document.getElementById('intro-screen-3').style.display = 'flex';
      });

      document.getElementById('proceed-button-2').addEventListener('click', function() {
        document.getElementById('intro-screen-3').style.display = 'none';
        document.getElementById('intro-screen-4').style.display = 'flex';
      });

      document.getElementById('proceed-button-3').addEventListener('click', function() {
        document.getElementById('intro-screen-4').style.display = 'none';
        document.getElementById('intro-screen-5').style.display = 'flex';
      });

      document.getElementById('proceed-button-4').addEventListener('click', function() {
        document.getElementById('intro-screen-5').style.display = 'none';
        document.getElementById('intro-screen-6').style.display = 'flex';
      });

      document.getElementById('final-start-button').addEventListener('click', function() {
        document.getElementById('intro-screen-6').style.display = 'none';
        document.getElementById('app-container').style.display = 'block';
        document.getElementById('profile-button').style.display = 'block';
        showWelcomeMessage();
        showNews();
      });

      // Bottom menu (delegazione eventi)
      document.addEventListener('click', function(e) {
        if(e.target.id === 'btn-news') showNews();
        if(e.target.id === 'btn-game') showGame();
        if(e.target.id === 'btn-edu') showEdu();
        if(e.target.id === 'btn-part') showParticipate();
      });
      
      // Pulsante profilo in alto
      document.getElementById('profile-button').addEventListener('click', showProfile);
    }

    // All'avvio
    document.addEventListener('DOMContentLoaded', function() {
      setupEventListeners();
      
      const savedName = localStorage.getItem('edita_username');
      if(savedName) {
        currentUser = savedName;
        document.getElementById('initial-screen').style.display = 'none';
        document.getElementById('welcome-screen').style.display = 'none';
        document.getElementById('app-container').style.display = 'block';
        document.getElementById('profile-button').style.display = 'block';
        loadProgress();
        showNews();
      }
    });
  </script>
</body>
</html>
