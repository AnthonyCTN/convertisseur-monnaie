# convertisseur-monnaie
convertisseur de monnaie fait en html css javascript



<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css">

</head>
<body>
    <div class="container">
        <h1>Outil de conversion de devises</h1>
      
        <input type="number" id="amount" placeholder="Montant en EUR">
      
        <select id="country">
          <option value="AUD" data-currency="Dollar australien (AUD)">Australie (AUD)</option>
          <option value="ZAR" data-currency="Rand sud-africain (ZAR)">Afrique du Sud (ZAR)</option>
          <option value="BRL" data-currency="Réal brésilien (BRL)">Brésil (BRL)</option>
          <option value="CAD" data-currency="Dollar canadien (CAD)">Canada (CAD)</option>
          <option value="CNY" data-currency="Yuan chinois (CNY)">Chine (CNY)</option>
          <option value="DKK" data-currency="Couronne danoise (DKK)">Danemark (DKK)</option>
          <option value="USD" data-currency="Dollar américain (USD)">États-Unis (USD)</option>
          <option value="HKD" data-currency="Dollar de Hong Kong (HKD)">Hong Kong (HKD)</option>
          <option value="INR" data-currency="Roupie indienne (INR)">Inde (INR)</option>
          <option value="MXN" data-currency="Peso mexicain (MXN)">Mexique (MXN)</option>
          <option value="NOK" data-currency="Couronne norvégienne (NOK)">Norvège (NOK)</option>
          <option value="NZD" data-currency="Dollar néo-zélandais (NZD)">Nouvelle-Zélande (NZD)</option>
          <option value="GBP" data-currency="Livre sterling (GBP)">Royaume-Uni (GBP)</option>
          <option value="CHF" data-currency="Franc suisse (CHF)">Suisse (CHF)</option>
          <option value="RUB" data-currency="Rouble russe (RUB)">Russie (RUB)</option>
          <option value="SEK" data-currency="Couronne suédoise (SEK)">Suède (SEK)</option>
          <option value="SGD" data-currency="Dollar de Singapour (SGD)">Singapour (SGD)</option>
          <option value="JPY" data-currency="Yen japonais (JPY)">Japon (JPY)</option>
        </select>
      
        <br><br>
      
        <button id="convertBtn">Convertir</button>
      
        <br><br>
      
        <div id="result"></div>
      
        <div class="icon">
          <i class="fas fa-star"></i>
        </div>
      
        <div class="icon">
          <i class="fas fa-heart"></i>
        </div>
      
        <div class="icon">
          <i class="fas fa-crown"></i>
        </div>

        <script>
        const convertBtn = document.getElementById('convertBtn');
        convertBtn.addEventListener('click', convertCurrency);
        
        function convertCurrency() {
          const amountInput = document.getElementById('amount');
          const amount = amountInput.value;
        
          if (isNaN(amount)) {
            alert("Veuillez entrer un montant valide.");
            return;
          }
        
          const countrySelect = document.getElementById('country');
          const selectedCountryOption = countrySelect.options[countrySelect.selectedIndex];
          const selectedCountry = selectedCountryOption.value;
          const selectedCountryName = selectedCountryOption.getAttribute("data-currency").split("(")[0].trim();
          const selectedCountrySymbol = getCurrencySymbol(selectedCountry);
        
          const conversionRates = {
            USD: { rate: 1.18, symbol: "$", name: "Dollar américain" },
            GBP: { rate: 0.85, symbol: "£", name: "Livre sterling" },
            JPY: { rate: 130.87, symbol: "¥", name: "Yen japonais" },
            CNY: { rate: 7.68, symbol: "¥", name: "Yuan chinois" },
            AUD: { rate: 1.59, symbol: "$", name: "Dollar australien" },
            CAD: { rate: 1.47, symbol: "$", name: "Dollar canadien" },
            SEK: { rate: 10.23, symbol: "kr", name: "Couronne suédoise" },
            CHF: { rate: 1.08, symbol: "CHF", name: "Franc suisse" },
            NZD: { rate: 1.71, symbol: "$", name: "Dollar néo-zélandais" },
            MXN: { rate: 24.81, symbol: "$", name: "Peso mexicain" },
            BRL: { rate: 6.38, symbol: "R$", name: "Réal brésilien" },
            INR: { rate: 87.26, symbol: "₹", name: "Roupie indienne" },
            ZAR: { rate: 17.11, symbol: "R", name: "Rand sud-africain" },
            NOK: { rate: 10.56, symbol: "kr", name: "Couronne norvégienne" },
            DKK: { rate: 7.44, symbol: "kr", name: "Couronne danoise" },
            SGD: { rate: 1.61, symbol: "$", name: "Dollar de Singapour" },
            HKD: { rate: 9.12, symbol: "HK$", name: "Dollar de Hong Kong" },
            RUB: { rate: 84.51, symbol: "₽", name: "Rouble russe" }
          };

        
          if (!(selectedCountry in conversionRates)) {
            alert("Veuillez sélectionner un pays de conversion valide.");
            return;
          }
        
          const rate = conversionRates[selectedCountry].rate;
          const result = (amount * rate).toFixed(2);
          const resultDiv = document.getElementById('result');
          resultDiv.textContent = `Montant converti : ${selectedCountrySymbol}${result} ${selectedCountryName}`;
        }
        
        function getCurrencySymbol(currencyCode) {
          const symbols = {
            USD: "$",
            GBP: "£",
            JPY: "¥",
            CNY: "¥",
            AUD: "$",
            CAD: "$",
            SEK: "kr",
            CHF: "CHF",
            NZD: "$",
            MXN: "$",
            BRL: "R$",
            INR: "₹",
            ZAR: "R",
            NOK: "kr",
            DKK: "kr",
            SGD: "$",
            HKD: "HK$",
            RUB: "₽"
          };
        
          return symbols[currencyCode] || "";
        }
    </script>
        
</body>
</html>
<style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f5f5f5;
      margin: 0;
      padding: 0;
    }
    
    .container {
      max-width: 400px;
      margin: 0 auto;
      padding: 20px;
      background-color: #ffffff;
      box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
      border-radius: 8px;
      box-sizing: border-box;
      text-align: center;
    }
    
    h1 {
      color: #333;
      margin-top: 0;
      margin-bottom: 20px;
    }
    
    #amount {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      margin-bottom: 20px;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
    
    #country {
      width: 100%;
      padding: 10px;
      font-size: 16px;
      margin-bottom: 20px;
      border: 1px solid #ddd;
      border-radius: 4px;
    }
    
    #convertBtn {
      padding: 10px 20px;
      font-size: 16px;
      background-color: #1d1f1d;
      color: white;
      border: none;
      border-radius: 4px;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
    
    #convertBtn:hover {
      background-color: #272727;
    }
    
    #result {
      font-size: 18px;
      margin-top: 30px;
    }
    
    .icon {
      display: inline-block;
      margin: 5px;
      font-size: 24px;
      color: #666;
      transition: color 0.3s ease;
    }
    
    .icon:hover {
      color: #121312;
    }
    

    .container > * {
      margin-bottom: 10px;
    }
    
    .icon:last-child {
      margin-bottom: 0;
    }
</style>
