<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>MoonsFX - Forex, Finance, and Growth eBooks</title>
  <link rel="stylesheet" href="style.css">
</head>
<body>
  <header>
    <h1>MoonsFX</h1>
    <p>Your go-to platform for Forex, Finance, and Growth eBooks</p>
  </header>
  <main>
    <section class="ebooks">
      <h2>Available eBooks</h2>
      <div class="ebook">
        <h3>Forex Fundamentals</h3>
        <p>Master the basics of Forex trading.</p>
        <p><strong>Price:</strong> $20</p>
        <button onclick="buyNow('Forex Fundamentals', 20)">Buy Now</button>
      </div>
      <div class="ebook">
        <h3>Finance Mastery</h3>
        <p>Unlock financial freedom with this guide.</p>
        <p><strong>Price:</strong> $25</p>
        <button onclick="buyNow('Finance Mastery', 25)">Buy Now</button>
      </div>
      <div class="ebook">
        <h3>Personal Growth Strategies</h3>
        <p>Achieve your goals with proven techniques.</p>
        <p><strong>Price:</strong> $15</p>
        <button onclick="buyNow('Personal Growth Strategies', 15)">Buy Now</button>
      </div>
    </section>
  </main>
  <footer>
    <p>Contact us: <a href="mailto:moonsfxke@yahoo.com">moonsfxke@yahoo.com</a></p>
  </footer>
  <script src="scripts.js"></script>
</body>
</html>
body {
  font-family: Arial, sans-serif;
  margin: 0;
  padding: 0;
  color: #333;
}

header {
  background-color: #4CAF50;
  color: white;
  text-align: center;
  padding: 20px;
}

main {
  padding: 20px;
}

.ebooks {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 20px;
}

.ebook {
  border: 1px solid #ddd;
  border-radius: 5px;
  padding: 15px;
  text-align: center;
}

.ebook h3 {
  margin: 0;
  color: #4CAF50;
}

button {
  background-color: #4CAF50;
  color: white;
  border: none;
  padding: 10px 20px;
  margin-top: 10px;
  cursor: pointer;
  border-radius: 5px;
}

button:hover {
  background-color: #45a049;
}

footer {
  text-align: center;
  padding: 10px;
  background-color: #f1f1f1;
  margin-top: 20px;
}
function buyNow(itemName, price) {
  const paypalForm = `
    <form action="https://www.paypal.com/cgi-bin/webscr" method="post" target="_blank">
      <input type="hidden" name="cmd" value="_xclick">
      <input type="hidden" name="business" value="moonsfxke@yahoo.com">
      <input type="hidden" name="item_name" value="${itemName}">
      <input type="hidden" name="amount" value="${price}">
      <input type="hidden" name="currency_code" value="USD">
      <input type="submit" value="Proceed to PayPal">
    </form>
  `;

  // Show PayPal form in a confirmation popup
  const confirmation = window.confirm(`You are about to purchase "${itemName}" for $${price}. Proceed?`);
  if (confirmation) {
    const popup = window.open('', '_blank', 'width=600,height=400');
    popup.document.write(paypalForm);
    popup.document.close();
    popup.document.forms[0].submit();
  }
}
