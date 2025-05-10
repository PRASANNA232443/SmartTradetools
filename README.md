<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Leverage Calculator + RR + Trade Size & Scaled TP Calculator</title>
  <style>
    :root {
      --primary-color: #4361ee;
      --primary-light: #4895ef;
      --primary-dark: #3f37c9;
      --secondary-color: #f72585;
      --success-color: #4cc9f0;
      --warning-color: #f8961e;
      --danger-color: #f94144;
      --text-dark: #2b2d42;
      --text-light: #8d99ae;
      --background-color: #f8f9fa;
      --card-bg: #ffffff;
      --border-radius: 12px;
      --box-shadow: 0 8px 30px rgba(0, 0, 0, 0.05);
      --transition: all 0.3s ease;
    }

    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
      background-color: var(--background-color);
      color: var(--text-dark);
      line-height: 1.6;
      padding: 20px;
    }

    .container {
      max-width: 1000px;
      margin: 0 auto;
      padding: 20px;
    }

    header {
      text-align: center;
      margin-bottom: 30px;
      padding: 20px 0;
    }

    h1 {
      font-size: 2.2rem;
      font-weight: 700;
      color: var(--primary-dark);
      margin-bottom: 10px;
    }

    h2 {
      font-size: 1.5rem;
      font-weight: 600;
      color: var(--primary-color);
      margin-bottom: 20px;
      border-bottom: 2px solid var(--primary-light);
      padding-bottom: 10px;
    }

    .card {
      background-color: var(--card-bg);
      border-radius: var(--border-radius);
      box-shadow: var(--box-shadow);
      padding: 25px;
      margin-bottom: 30px;
      transition: var(--transition);
    }

    .card:hover {
      box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
      transform: translateY(-5px);
    }
    
    #leverage-calculator {
      background: linear-gradient(135deg, #e0f7fa, #b2ebf2);
      border-left: 5px solid #00bcd4;
    }
    
    #scaled-tp-section {
      background: linear-gradient(135deg, #e8f5e9, #c8e6c9);
      border-left: 5px solid #4caf50;
    }

    .form-group {
      margin-bottom: 20px;
    }

    label {
      display: block;
      font-weight: 600;
      margin-bottom: 8px;
      color: var(--text-dark);
    }

    .input-group {
      position: relative;
    }

    input[type="number"] {
      width: 100%;
      padding: 12px 15px;
      border: 1px solid #ddd;
      border-radius: 8px;
      font-size: 16px;
      transition: var(--transition);
      background-color: #f9f9f9;
    }

    input[type="number"]:focus {
      outline: none;
      border-color: var(--primary-light);
      box-shadow: 0 0 0 3px rgba(67, 97, 238, 0.15);
      background-color: #fff;
    }

    .slider-container {
      margin-top: 10px;
    }

    input[type="range"] {
      width: 100%;
      height: 8px;
      border-radius: 5px;
      -webkit-appearance: none;
      background: linear-gradient(to right, var(--primary-light), var(--primary-color));
    }

    input[type="range"]::-webkit-slider-thumb {
      -webkit-appearance: none;
      width: 20px;
      height: 20px;
      border-radius: 50%;
      background: var(--primary-color);
      cursor: pointer;
      border: 3px solid white;
      box-shadow: 0 0 0 1px var(--primary-color);
    }

    .slider-value {
      text-align: right;
      font-weight: 600;
      color: var(--primary-color);
      margin-top: 5px;
    }

    small {
      display: block;
      color: var(--text-light);
      font-size: 13px;
      margin-top: 6px;
    }

    .btn {
      display: block;
      width: 100%;
      padding: 14px;
      border: none;
      border-radius: 8px;
      font-size: 16px;
      font-weight: 600;
      cursor: pointer;
      transition: var(--transition);
      text-align: center;
      text-transform: uppercase;
      letter-spacing: 0.5px;
    }

    .btn-primary {
      background-color: var(--primary-color);
      color: white;
    }

    .btn-primary:hover {
      background-color: var(--primary-dark);
      transform: translateY(-2px);
      box-shadow: 0 5px 15px rgba(67, 97, 238, 0.3);
    }

    .result-box {
      margin-top: 25px;
      background: linear-gradient(135deg, #fff9c4, #fff59d);
      border-left: 4px solid #fbc02d;
      padding: 15px;
      border-radius: 8px;
      font-weight: 500;
      box-shadow: 0 4px 10px rgba(251, 192, 45, 0.15);
    }

    .result-value {
      font-weight: 700;
      color: var(--primary-color);
    }

    .rr-box {
      background: linear-gradient(135deg, #e3f2fd, #bbdefb);
      padding: 20px;
      border-radius: 10px;
      margin-bottom: 20px;
      border: 1px solid rgba(33, 150, 243, 0.3);
      box-shadow: 0 4px 15px rgba(33, 150, 243, 0.1);
    }

    table {
      width: 100%;
      border-collapse: collapse;
      margin-top: 25px;
      font-size: 15px;
      border-radius: 8px;
      overflow: hidden;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.05);
    }

    th, td {
      padding: 12px 15px;
      text-align: center;
    }

    th {
      background: linear-gradient(to right, #7e57c2, #5e35b1);
      color: white;
      font-weight: 600;
      text-transform: uppercase;
      font-size: 14px;
      letter-spacing: 0.5px;
    }

    td {
      border-bottom: 1px solid #eee;
    }

    tr:last-child td {
      border-bottom: none;
    }

    tr:nth-child(even) {
      background-color: #f9faff;
    }

    .summary {
      margin-top: 25px;
      background: linear-gradient(135deg, #f3e5f5, #e1bee7);
      padding: 20px;
      border-radius: 10px;
      font-weight: 500;
      line-height: 1.8;
      border-left: 4px solid #9c27b0;
      box-shadow: 0 4px 15px rgba(156, 39, 176, 0.1);
    }

    .summary b {
      color: var(--primary-dark);
    }

    .emoji {
      font-size: 18px;
      margin-right: 5px;
    }

    .two-columns {
      display: flex;
      gap: 20px;
      margin-bottom: 20px;
    }

    .column {
      flex: 1;
    }

    .input-with-label {
      position: relative;
    }

    .input-with-label span {
      position: absolute;
      right: 15px;
      top: 50%;
      transform: translateY(-50%);
      color: var(--text-light);
      font-weight: 600;
    }

    /* Responsive adjustments */
    @media (max-width: 768px) {
      .two-columns {
        flex-direction: column;
      }
      
      .container {
        padding: 10px;
      }
      
      .card {
        padding: 20px;
      }
      
      h1 {
        font-size: 1.8rem;
      }
      
      h2 {
        font-size: 1.3rem;
      }
    }
  </style>
</head>
<body>












    <!-- Leverage Calculator Section -->
    <section class="card" id="leverage-calculator">
      <h2>Leverage Calculator</h2>

      <!-- RR Section -->
      <div class="rr-box">
        <h2>Risk/Reward Calculator</h2>
        
        <div class="two-columns">
          <div class="column">
            <div class="form-group">
              <label for="entryPrice">Entry Price:</label>
              <div class="input-group">
                <input type="number" id="entryPrice" placeholder="Enter entry price" autocomplete="off">
              </div>
            </div>
          </div>
          
          <div class="column">
            <div class="form-group">
              <label for="tpPrice">Full TP Price:</label>
              <div class="input-group">
                <input type="number" id="tpPrice" placeholder="Enter full take profit price" autocomplete="off">
              </div>
            </div>
          </div>
        </div>

        <div class="form-group">
          <label for="slPrice">Stop Loss Price:</label>
          <div class="input-group">
            <input type="number" id="slPrice" placeholder="Enter stop loss price" autocomplete="off">
          </div>
        </div>

        <button type="button" class="btn btn-primary" onclick="calculateRR()">Calculate Risk/Reward</button>
        
        <div class="result-box" id="rrResult">
          <div class="result-value">Risk/Reward = ?</div>
        </div>
      </div>
















      <div class="form-group">
        <label for="capital">Capital (USDT):</label>
        <div class="input-group">
          <input type="number" id="capital" placeholder="Enter your total capital" autocomplete="off">
        </div>
        <small>This is the total amount of money you have for trading.</small>
      </div>

      <div class="form-group">
        <label for="marginSlider">Margin (%):</label>
        <div class="slider-container">
          <input type="range" id="marginSlider" min="0" max="100" value="0" aria-valuemin="0" aria-valuemax="100" aria-valuenow="0">
          <div class="slider-value">Selected Margin: <span id="marginValue">0%</span></div>
        </div>
      </div>

      <div class="form-group">
        <label for="riskSlider">Risk (%):</label>
        <div class="slider-container">
          <input type="range" id="riskSlider" min="0" max="100" value="50" aria-valuemin="0" aria-valuemax="100" aria-valuenow="50">
          <div class="slider-value">Selected Risk: <span id="riskValue">50%</span></div>
        </div>
      </div>

      <div class="form-group">
        <label for="stopLoss">Stop Loss (%):</label>
        <div class="input-with-label">
          <input type="number" id="stopLoss" placeholder="Enter stop loss percentage" autocomplete="off">
          <span>%</span>
        </div>
        <small>The % of price movement that will trigger stop loss.</small>
      </div>

      <button type="button" class="btn btn-primary" onclick="calculateLeverage()">Calculate Leverage</button>

      <div class="result-box" id="result">
        <div class="result-value">Leverage = ?</div>
      </div>
    </section>







    <!-- Scaled TP Calculator Section -->
    <section class="card" id="scaled-tp-section">
      <h2>Scaled Take-Profit (TP) Calculator</h2>

      <div class="two-columns">
        <div class="column">
          <div class="form-group">
            <label for="balance">Account Balance (USDT):</label>
            <div class="input-with-label">
              <input type="number" id="balance" value="100" autocomplete="off">
              <span>USDT</span>
            </div>
          </div>
        </div>
        
        <div class="column">
          <div class="form-group">
            <label for="risk">Risk per Trade (%):</label>
            <div class="input-with-label">
              <input type="number" id="risk" value="1" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
      </div>
      
      <div class="form-group">
        <label for="rr">Risk-Reward Ratio (RR):</label>
        <input type="number" step="0.1" id="rr" value="2" autocomplete="off">
      </div>

      <div class="two-columns">
        <div class="column">
          <div class="form-group">
            <label for="tp1">TP1 % of Full Position:</label>
            <div class="input-with-label">
              <input type="number" id="tp1" value="50" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
        
        <div class="column">
          <div class="form-group">
            <label for="tp2">TP2 % of Remaining:</label>
            <div class="input-with-label">
              <input type="number" id="tp2" value="30" autocomplete="off">
              <span>%</span>
            </div>
          </div>
        </div>
      </div>

      <div class="form-group">
        <label for="tp3">TP3 % of Remaining:</label>
        <div class="input-with-label">
          <input type="number" id="tp3" value="20" autocomplete="off">
          <span>%</span>
        </div>
      </div>

      <button type="button" class="btn btn-primary" onclick="calculateTP()">Calculate Scaled Take Profit</button>

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
  </div>

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
        `<p><span class='emoji'>📊</span> Leverage = <span class='result-value'>${leverage}x</span></p>
        <p><span class='emoji'>💵</span> Margin = <span class='result-value'>$${marginUSD.toFixed(2)}</span></p>
        <p><span class='emoji'>⚠️</span> Risk = <span class='result-value'>$${riskUSD.toFixed(2)}</span></p>
        <p><span class='emoji'>🔄</span> Trade Size = <span class='result-value'>$${tradeSize}</span></p>
        <p><span class='emoji'>🎯</span> Full Take Profit = <span class='result-value'>$${fullTP}</span></p>`;
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
        `<p><span class='emoji'>⚠️</span> <b>Risk Amount(SL):</b> $${riskAmt.toFixed(2)}</p>
        <p><span class='emoji'>📈</span> <b>Full Profit (No Scaling):</b> $${totalProfit.toFixed(2)}</p>
        <p><span class='emoji'>🔻</span> <b>Scaled TP Profit:</b> $${totalScaled.toFixed(2)}</p>`;
    }
  </script>
</body>
</html>
