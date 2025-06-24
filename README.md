<!DOCTYPE html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8">
  <title>حاسبة الكوريان - كوريان كاسل</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 40px;
      background-color: #f9f9f9;
      direction: rtl;
    }
    .container {
      background: white;
      padding: 20px;
      border-radius: 12px;
      max-width: 350px;
      margin: auto;
      box-shadow: 0 0 10px #ccc;
      text-align: right;
    }
    input, button {
      width: 100%;
      padding: 10px;
      margin: 10px 0;
      font-size: 16px;
    }
    h2 {
      text-align: center;
    }
    .note {
      color: #666;
      font-size: 14px;
      margin-bottom: 5px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h2>🔧 حاسبة كوريان كاسل</h2>

    <label>كود اللوح:</label>
    <input type="text" id="code" placeholder="مثال: A_106">

    <label>عدد الأمتار المطلوبة:</label>
    <input type="number" id="meters" step="0.01">

    <button onclick="calculate()">احسب</button>

    <h3>📊 النتيجة:</h3>
    <p>عدد الألواح المطلوبة: <span id="sheets">-</span></p>
    <p>سعر اللوح: <span id="price">-</span> دينار كويتي</p>
    <p>إجمالي السعر: <span id="total">-</span> دينار كويتي</p>
    <p class="note">* تأكد من كتابة الكود بشكل صحيح</p>
  </div>

  <script>
    const priceMap = {
      "A_106": 65,
      "A_143": 80,
      "A_195": 95,
      "A_250": 115
    };

    function calculate() {
      let code = document.getElementById("code").value.trim().toUpperCase();
      let meters = parseFloat(document.getElementById("meters").value);
      let sheetLength = 3.65;

      if (!priceMap.hasOwnProperty(code)) {
        alert("⚠️ الكود غير معروف. من فضلك تأكد من إدخاله بشكل صحيح.");
        return;
      }

      if (isNaN(meters) || meters <= 0) {
        alert("⚠️ من فضلك أدخل عدد الأمتار بشكل صحيح.");
        return;
      }

      let price = priceMap[code];
      let numSheets = Math.ceil(meters / sheetLength);
      let total = numSheets * price;

      document.getElementById("sheets").innerText = numSheets;
      document.getElementById("price").innerText = price;
      document.getElementById("total").innerText = total.toFixed(2);
    }
  </script>

</body>
</html>
