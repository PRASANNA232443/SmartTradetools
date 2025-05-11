
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>SmartTrade Tools - Trading Calculator Suite</title>
  <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.0.0/css/all.min.css">
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500;600;700&display=swap" rel="stylesheet">
  <style>
    :root {
      --primary: #4361ee;
      --primary-light: #4895ef;
      --primary-dark: #3a0ca3;
      --secondary: #f72585;
      --success: #4cc9f0;
      --warning: #fca311;
      --danger: #e71d36;
      --info: #00b4d8;
      --dark: #2b2d42;
      --light: #f8f9fa;
      --text-muted: #6c757d;
      --border-color: #e9ecef;
      --card-bg: #ffffff;
      --gradient-primary: linear-gradient(135deg, #4361ee, #3a0ca3);
      --gradient-secondary: linear-gradient(135deg, #f72585, #b5179e);
      --box-shadow: 0 10px 30px rgba(0, 0, 0, 0.08);
      --box-shadow-hover: 0 15px 35px rgba(0, 0, 0, 0.12);
      --border-radius: 16px;
      --transition: all 0.3s ease;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Poppins', sans-serif;
      background-color: #f0f2f5; 
      color: var(--dark);
      line-height: 1.6;
      padding: 0;
      min-height: 100vh;
      background-image: linear-gradient(135deg, #f5f7fa 0%, #c3cfe2 100%);
      background-attachment: fixed;
    }

    .container {
      max-width: 1140px;
      margin: 0 auto;
      padding: 30px 20px;
      position: relative;
    }

    header {
      text-align: center;
      padding: 0 0 30px;
      background: var(--gradient-primary);
      margin-bottom: 50px;
      padding: 60px 0;
      color: white;
      border-radius: 0 0 30px 30px;
      box-shadow: var(--box-shadow);
      position: relative;
      overflow: hidden;
    }

    header::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      background-image: url("data:image/svg+xml,%3Csvg width='100' height='100' viewBox='0 0 100 100' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M11 18c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm48 25c3.866 0 7-3.134 7-7s-3.134-7-7-7-7 3.134-7 7 3.134 7 7 7zm-43-7c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm63 31c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM34 90c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zm56-76c1.657 0 3-1.343 3-3s-1.343-3-3-3-3 1.343-3 3 1.343 3 3 3zM12 86c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm28-65c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm23-11c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-6 60c2.21 0 4-1.79 4-4s-1.79-4-4-4-4 1.79-4 4 1.79 4 4 4zm29 22c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zM32 63c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm57-13c2.76 0 5-2.24 5-5s-2.24-5-5-5-5 2.24-5 5 2.24 5 5 5zm-9-21c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM60 91c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM35 41c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2zM12 60c1.105 0 2-.895 2-2s-.895-2-2-2-2 .895-2 2 .895 2 2 2z' fill='rgba(255,255,255,0.1)' fill-rule='evenodd'/%3E%3C/svg%3E");
      z-index: 0;
    }

    .header-content {
      position: relative;
      z-index: 1;
    }

    h1 {
      font-size: 2.8rem;
      font-weight: 700;
      margin-bottom: 10px;
      text-transform: uppercase;
      letter-spacing: 1px;
    }

    .header-subtitle {
      font-size: 1.2rem;
      opacity: 0.9;
      max-width: 600px;
      margin: 0 auto;
    }

    h2 {
      font-size: 1.8rem;
      font-weight: 600;
      color: var(--primary-dark);
      margin-bottom: 25px;
      position: relative;
      display: inline-block;
    }

    h2::after {
      content: '';
      position: absolute;
      bottom: -10px;
      left: 0;
      width: 60px;
      height: 4px;
      background: var(--gradient-primary);
      border-radius: 2px;
    }

    .card {
      border-radius: var(--border-radius);
      box-shadow: var(--box-shadow);
      padding: 35px;
      margin-bottom: 40px;
      transition: var(--transition);
      border: 1px solid var(--border-color);
      position: relative;
      overflow: hidden;
    }
    
    .card:nth-of-type(1) {
      background: linear-gradient(135deg, #e0f7fa, #b2ebf2);
    }
    
    .card:nth-of-type(2) {
      background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
    }

    .card:hover {
      box-shadow: var(--box-shadow-hover);
      transform: translateY(-5px);
    }

    .card-header {
      display: flex;
      align-items: center;
      margin-bottom: 25px;
    }

    .card-icon {
      width: 50px;
      height: 50px;
      display: flex;
      align-items: center;
      justify-content: center;
      border-radius: 12px;
      margin-right: 15px;
      font-size: 1.5rem;
      color: white;
    }

    .leverage-icon {
      background: linear-gradient(135deg, #4cc9f0, #0077b6);
    }

    .rr-icon {
      background: linear-gradient(135deg, #fca311, #e85d04);
    }

    .tp-icon {
      background: linear-gradient(135deg, #70e000, #38b000);
    }

    .card::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: var(--gradient-primary);
    }

    .rr-box {
      background: linear-gradient(135deg, #fcf5ef, #fff8f3);
      padding: 30px;
      border-radius: var(--border-radius);
      margin-bottom: 40px;
      border: 1px solid var(--border-color);
      box-shadow: var(--box-shadow);
      position: relative;
      overflow: hidden;
    }

    .rr-box::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 5px;
      background: linear-gradient(135deg, #fca311, #e85d04);
    }

    .form-group {
      margin-bottom: 25px;
    }

    label {
      display: block;
      font-weight: 600;
      margin-bottom: 10px;
      color: var(--dark);
      font-size: 0.95rem;
    }

    .input-group {
      position: relative;
    }

    input[type="number"] {
      width: 100%;
      padding: 12px 20px;
      border: 2px solid var(--border-color);
      border-radius: 12px;
      font-size: 1rem;
      transition: var(--transition);
      background-color: #f8f9fa;
      font-family: 'Poppins', sans-serif;
    }

    input[type="number"]:focus {
      outline: none;
      border-color: var(--primary);
      box-shadow: 0 0 0 4px rgba(67, 97, 238, 0.15);
      background-color: #fff;
    }

    .slider-container {
      margin-top: 12px;
    }

    input[type="range"] {
      width: 100%;
      height: 8px;
      border-radius: 10px;
      -webkit-appearance: none;
      background: linear-gradient(to right, var(--primary-light), var(--primary));
      cursor: pointer;
    }

    input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 22px;
      height: 22px;
      border-radius: 50%;
      background: var(--gradient-primary);
      cursor: pointer;
      border: 3px solid white;
      box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.1), 0 3px 5px rgba(0, 0, 0, 0.15);
    }

    .slider-value {
      display: flex;
      justify-content: space-between;
      font-weight: 500;
      color: var(--dark);
      margin-top: 8px;
      font-size: 0.9rem;
    }

    .slider-value .value {
      color: var(--primary);
      font-weight: 600;
    }

    small {
      display: block;
      color: var(--text-muted);
      font-size: 0.85rem;
      margin-top: 8px;
      font-weight: 400;
    }

    .btn {
      display: inline-block;
      width: 100%;
      padding: 15px 20px;
      border: none;
      border-radius: 12px;
      font-size: 1rem;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      text-align: center;
      text-transform: uppercase;
      letter-spacing: 0.5px;
      font-family: 'Poppins', sans-serif;
      position: relative;
      overflow: hidden;
      z-index: 1;
    }

    .btn::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(255, 255, 255, 0.1);
      z-index: -1;
      transform: scaleX(0);
      transform-origin: right;
      transition: transform 0.5s ease;
    }

    .btn:hover::before {
      transform: scaleX(1);
      transform-origin: left;
    }

    .btn-primary {
      background: var(--gradient-primary);
      color: white;
      box-shadow: 0 4px 15px rgba(67, 97, 238, 0.3);
    }

    .btn-primary:hover {
      box-shadow: 0 8px 25px rgba(67, 97, 238, 0.4);
      transform: translateY(-2px);
    }

    .result-box {
      margin-top: 30px;
      background: linear-gradient(135deg, #fff9c4, #fff59d);
      border-radius: 12px;
      padding: 20px;
      border: 1px solid #fbc02d30;
      font-weight: 500;
      box-shadow: 0 4px 10px rgba(251, 192, 45, 0.15);
      position: relative;
      overflow: hidden;
    }

    .result-box::before {
      content: '';
      position: absolute;
      top: 0;
      left: 0;
      width: 5px;
      height: 100%;
      background: var(--gradient-primary);
    }

    .result-value {
      font-weight: 700;
      color: var(--primary-dark);
    }

    table {
      width: 100%;
      border-collapse: separate;
      border-spacing: 0;
      margin-top: 30px;
      font-size: 0.95rem;
      border-radius: 12px;
      overflow: hidden;
      box-shadow: 0 4px 15px rgba(0, 0, 0, 0.05);
    }

    th, td {
      padding: 15px 20px;
      text-align: center;
    }

    th {
      background: var(--gradient-primary);
      color: white;
      font-weight: 600;
      text-transform: uppercase;
      font-size: 0.85rem;
      letter-spacing: 1px;
    }

    td {
      border-bottom: 1px solid var(--border-color);
      background-color: white;
    }

    tr:last-child td {
      border-bottom: none;
    }

    tr:hover td {
      background-color: #f8f9ff;
    }

    .summary {
      margin-top: 30px;
      background: linear-gradient(135deg, #f3e5f5, #e1bee7);
      padding: 25px;
      border-radius: 12px;
      font-weight: 500;
      line-height: 1.8;
      border: 1px solid rgba(156, 39, 176, 0.2);
      box-shadow: 0 4px 15px rgba(156, 39, 176, 0.1);
    }

    .summary p {
      margin-bottom: 10px;
    }

    .summary p:last-child {
      margin-bottom: 0;
    }

    .summary b {
      color: var(--primary-dark);
    }

    .two-columns {
      display: flex;
      gap: 25px;
      margin-bottom: 25px;
    }

    .column {
      flex: 1;
    }

    .input-with-label {
      position: relative;
    }

    .input-with-label span {
      position: absolute;
      right: 20px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--text-muted);
      font-weight: 500;
      font-size: 0.9rem;
    }

    .card-badge {
      position: absolute;
      top: 20px;
      right: 20px;
      background: rgba(67, 97, 238, 0.1);
      color: var(--primary);
      padding: 5px 15px;
      border-radius: 20px;
      font-size: 0.8rem;
      font-weight: 600;
    }

    .icon-box {
      display: inline-flex;
      align-items: center;
      justify-content: center;
      width: 35px;
      height: 35px;
      border-radius: 50%;
      background: rgba(67, 97, 238, 0.1);
      color: var(--primary);
      margin-right: 8px;
    }

    .emoji {
      font-style: normal;
    }

    footer {
      text-align: center;
      margin-top: 50px;
      padding: 30px 0;
      color: var(--text-muted);
      font-size: 0.9rem;
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
      .two-columns {
        flex-direction: column;
        gap: 15px;
      }
      
      .container {
        padding: 15px;
      }
      
      .card, .rr-box {
        padding: 25px;
      }
      
      h1 {
        font-size: 2rem;
      }
      
      h2 {
        font-size: 1.5rem;
      }

      header {
        padding: 40px 0;
      }
    }
  </style>




  
        <header>
          <div class="header-content">
            <h1>Smart Trade Tools</h1>
            <div class="header-subtitle">Optimize your trading strategy with our advanced calculators</div>
             <div class="header-subtitle">This tools created by Prasanna Indrajith</div>
            
          </div>
        </header>

      

    
    <div class="rr-box">
      <div class="card-header">
        <div class="card-icon rr-icon">
          <i class="fas fa-balance-scale"></i>
        </div>
        <h2>Risk/Reward Calculator</h2>
      </div>
      
      <div class="two-columns">
        <div class="column">
          <div class="form-group">
            <label for="entryPrice"><i class="fas fa-sign-in-alt"></i> Entry Price:</label>
            <div class="input-group">
              <input type="number" id="entryPrice" placeholder="Enter entry price" autocomplete="off">
            </div>
          </div>
        </div>
        
        <div class="column">
          <div class="form-group">
            <label for="tpPrice"><i class="fas fa-arrow-circle-up"></i> Full TP Price:</label>
            <div class="input-group">
              <input type="number" id="tpPrice" placeholder="Enter full take profit price" autocomplete="off">
            </div>
          </div>
        </div>
      </div>

      <div class="form-group">
        <label for="slPrice"><i class="fas fa-arrow-circle-down"></i> Stop Loss Price:</label>
        <div class="input-group">
          <input type="number" id="slPrice" placeholder="Enter stop loss price" autocomplete="off">
        </div>
      </div>

      <button type="button" class="btn btn-primary" onclick="calculateRR()">
        <i class="fas fa-calculator"></i> Calculate Risk/Reward
      </button>
      
      <div class="result-box" id="rrResult">
        <div class="result-value">Risk/Reward = ?</div>
      </div>
    </div>





  
    <section class="card">
      <div class="card-badge">Essential</div>
      <div class="card-header">
        <div class="card-icon leverage-icon">
          <i class="fas fa-chart-line"></i>
        </div>
        <h2>Leverage Calculator</h2>
      </div>

      <div class="form-group">
        <label for="capital"><i class="fas fa-coins"></i> Capital (USDT):</label>
        <div class="input-group">
          <input type="number" id="capital" placeholder="Enter your total capital" autocomplete="off">
        </div>
        <small>This is the total amount of money you have for trading.</small>
      </div>

      <div class="form-group">
        <label for="marginSlider"><i class="fas fa-percentage"></i> Margin (%):</label>
        <div class="slider-container">
          <input type="range" id="marginSlider" min="0" max="100" value="0" aria-valuemin="0" aria-valuemax="100" aria-valuenow="0">
          <div class="slider-value">
            <span>Margin</span>
            <span class="value" id="marginValue">0%</span>
          </div>
        </div>
      </div>

      <div class="form-group">
        <label for="riskSlider"><i class="fas fa-exclamation-triangle"></i> Risk (%):</label>
        <div class="slider-container">
          <input type="range" id="riskSlider" min="0" max="100" value="50" aria-valuemin="0" aria-valuemax="100" aria-valuenow="50">
          <div class="slider-value">
            <span>Risk</span>
            <span class="value" id="riskValue">50%</span>
          </div>
        </div>
      </div>

      <div class="form-group">
        <label for="stopLoss"><i class="fas fa-shield-alt"></i> Stop Loss (%):</label>
        <div class="input-with-label">
          <input type="number" id="stopLoss" placeholder="Enter stop loss percentage" autocomplete="off">
          <span>%</span>
        </div>
        <small>The % of price movement that will trigger stop loss.</small>
      </div>

      <button type="button" class="btn btn-primary" onclick="calculateLeverage()">
        <i class="fas fa-calculator"></i> Calculate Leverage
      </button>

      <div class="result-box" id="result">
        <div class="result-value">Leverage = ?</div>
      </div>
    </section>












    <section class="card">
      <div class="card-badge">Pro</div>
      <div class="card-header">
        <div class="card-icon tp-icon">
          <i class="fas fa-layer-group"></i>
        </div>
        <h2>Scaled Take-Profit (TP) Calculator</h2>
      </div>

      <div class="two-columns">
        <div class="column">
          <div class="form-group">
            <label for="balance"><i class="fas fa-wallet"></i> Account Balance (USDT):</label>
            <div class="input-with-label">
              <input type="number" id="balance" value="100" autocomplete="off">
              <span>USDT</span>
            </div>
          </div>
        </div>
        
        <div class="column">
          <div class="form-group">
            <label for="risk"><i class="fas fa-exclamation-triangle"></i> Risk per Trade (%):</label>
            <div class="input-with-label">
              <input type="number" id="risk" value="1" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
      </div>
      
      <div class="form-group">
        <label for="rr"><i class="fas fa-balance-scale"></i> Risk-Reward Ratio (RR):</label>
        <input type="number" step="0.1" id="rr" value="2" autocomplete="off">
      </div>

      <div class="two-columns">
        <div class="column">
          <div class="form-group">
            <label for="tp1"><i class="fas fa-tag"></i> TP1 % of Full Position:</label>
            <div class="input-with-label">
              <input type="number" id="tp1" value="50" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
        
        <div class="column">
          <div class="form-group">
            <label for="tp2"><i class="fas fa-tag"></i> TP2 % of Remaining:</label>
            <div class="input-with-label">
              <input type="number" id="tp2" value="30" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
      </div>

      <div class="form-group">
        <label for="tp3"><i class="fas fa-tag"></i> TP3 % of Remaining:</label>
        <div class="input-with-label">
          <input type="number" id="tp3" value="20" autocomplete="off">
          <span>%</span>
        </div>
      </div>

      <button type="button" class="btn btn-primary" onclick="calculateTP()">
        <i class="fas fa-calculator"></i> Calculate Scaled Take Profit
      </button>

      <table id="resultTable" style="display:none;">
        <thead>
          <tr>
            <th>TP Level</th>
            <th>Units Closed</th>
            <th>Profit per Unit (USDT)</th>
            <th>Profit (USDT)</th>
          </tr>
        </thead>
        <tbody id="results"></tbody>
      </table>

      <div id="summary" class="summary"></div>
    </section>

    <footer>
      <p>© 2025 SmartTrade Tools | Version 2.0</p>
    </footer>
  

  <script>
    // Leverage Calculator Scripts
    const marginSlider = document.getElementById("marginSlider");
    const riskSlider = document.getElementById("riskSlider");
    const marginValue = document.getElementById("marginValue");
    const riskValue = document.getElementById("riskValue");

    marginSlider.oninput = function () {
      marginValue.textContent = this.value + "%";
    }

    riskSlider.oninput = function () {
      riskValue.textContent = this.value + "%";
    }

    let globalRR = null;

    function calculateRR() {
      let entry = parseFloat(document.getElementById("entryPrice").value);
      let tp = parseFloat(document.getElementById("tpPrice").value);
      let sl = parseFloat(document.getElementById("slPrice").value);

      if (isNaN(entry) || isNaN(tp) || isNaN(sl) || (entry - sl) === 0) {
        document.getElementById("rrResult").innerHTML = "<div class='result-value'>Enter valid values for RR.</div>";
        return;
      }

      globalRR = (Math.abs(tp - entry) / Math.abs(entry - sl)).toFixed(2);
      document.getElementById("rrResult").innerHTML = `<div class='result-value'>Risk/Reward = ${globalRR}</div>`;
    }

    function calculateLeverage() {
      let capital = parseFloat(document.getElementById("capital").value);
      let marginPercent = parseFloat(marginSlider.value);
      let riskPercent = parseFloat(riskSlider.value);
      let stopLossPercent = parseFloat(document.getElementById("stopLoss").value);

      if (isNaN(capital) || isNaN(stopLossPercent) || stopLossPercent === 0) {
        document.getElementById("result").innerHTML = "<div class='result-value'>Please enter valid values.</div>";
        return;
      }

      let marginUSD = (capital * marginPercent) / 100;
      let riskUSD = (marginUSD * riskPercent) / 100;
      let leverage = (riskUSD / (marginUSD * (stopLossPercent / 100))).toFixed(2);

      // Trade size = Margin * Leverage
      let tradeSize = (marginUSD * leverage).toFixed(2);

      // Full TP USD = Risk USD * RR
      let fullTP = globalRR ? (riskUSD * globalRR).toFixed(2) : "?";

      document.getElementById("result").innerHTML = 
        `<p><span class="icon-box"><i class="fas fa-chart-line"></i></span> Leverage = <span class='result-value'>${leverage}x</span></p>
        <p><span class="icon-box"><i class="fas fa-coins"></i></span> Margin = <span class='result-value'>${marginUSD.toFixed(2)}</span></p>
        <p><span class="icon-box"><i class="fas fa-exclamation-triangle"></i></span> Risk = <span class='result-value'>${riskUSD.toFixed(2)}</span></p>
        <p><span class="icon-box"><i class="fas fa-exchange-alt"></i></span> Trade Size = <span class='result-value'>${tradeSize}</span></p>
        <p><span class="icon-box"><i class="fas fa-bullseye"></i></span> Full Take Profit = <span class='result-value'>${fullTP}</span></p>`;
    }

    // Scaled TP Calculator Scripts
    function calculateTP() {
      let balance = parseFloat(document.getElementById("balance").value);
      let risk = parseFloat(document.getElementById("risk").value);
      let rr = parseFloat(document.getElementById("rr").value);
      let tp1_pct = parseFloat(document.getElementById("tp1").value) / 100;
      let tp2_pct_remain = parseFloat(document.getElementById("tp2").value) / 100;
      let tp3_pct_remain = parseFloat(document.getElementById("tp3").value) / 100;

      let riskAmt = balance * (risk / 100);
      let totalProfit = riskAmt * rr;

      let totalUnits = 100;
      let profitPerUnit = totalProfit / totalUnits;

      let tp1_units = totalUnits * tp1_pct;
      let remain1 = totalUnits - tp1_units;

      let tp2_units = remain1 * tp2_pct_remain;
      let remain2 = remain1 - tp2_units;

      let tp3_units = remain2 * tp3_pct_remain;

      let tp1_profit = tp1_units * profitPerUnit;
      let tp2_profit = tp2_units * profitPerUnit;
      let tp3_profit = tp3_units * profitPerUnit;

      let totalScaled = tp1_profit + tp2_profit + tp3_profit;

      let results = 
        `<tr><td>TP1</td><td>${tp1_units.toFixed(2)}</td><td>${profitPerUnit.toFixed(2)}</td><td>${tp1_profit.toFixed(2)}</td></tr>` +
        `<tr><td>TP2</td><td>${tp2_units.toFixed(2)}</td><td>${profitPerUnit.toFixed(2)}</td><td>${tp2_profit.toFixed(2)}</td></tr>` +
        `<tr><td>TP3</td><td>${tp3_units.toFixed(2)}</td><td>${profitPerUnit.toFixed(2)}</td><td>${tp3_profit.toFixed(2)}</td></tr>`;

      document.getElementById("results").innerHTML = results;
      document.getElementById("resultTable").style.display = "table";
      document.getElementById("summary").innerHTML = 
        `<p><span class="icon-box"><i class="fas fa-exclamation-triangle"></i></span> <b>Risk Amount(SL):</b> ${riskAmt.toFixed(2)}</p>
        <p><span class="icon-box"><i class="fas fa-chart-line"></i></span> <b>Full Profit (No Scaling):</b> ${totalProfit.toFixed(2)}</p>
        <p><span class="icon-box"><i class="fas fa-layer-group"></i></span> <b>Scaled TP Profit:</b> ${totalScaled.toFixed(2)}</p>`;
    }
