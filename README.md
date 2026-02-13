<html lang="ru">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1" />
  <title>Валентинка с летающими сердцами</title>
  <style>
    body, html {
      margin: 0;
      height: 100vh;
      overflow: hidden;
      background: #000;
      font-family: 'Montserrat', sans-serif;
      position: relative;
    }

   .container {
      position: fixed;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      background: rgba(255 255 255 / 0.95);
      border-radius: 20px;
      padding: 30px 30px 40px 30px;
      box-shadow: 0 10px 30px rgba(0,0,0,0.2);
      min-width: 320px;
      max-width: 380px;
      text-align: center;
      color: #332f6f;
      user-select: none;
      z-index: 10;
      overflow: hidden;
      position: relative;
    }

  .container h1 {
      font-weight: 700;
      font-size: 28px;
      margin-bottom: 8px;
    }

   .container p {
      font-weight: 400;
      font-size: 17px;
      margin-bottom: 25px;
      color: #000;
    }

   button {
      cursor: pointer;
      font-weight: 700;
      font-size: 16px;
      border-radius: 9999px;
      border: none;
      padding: 12px 26px;
      margin: 0 10px;
      transition: all 0.3s ease;
      user-select: none;
      position: relative;
      z-index: 10;
    }

  #yesBtn {
      background: #5459db;
      color: #fff;
      box-shadow: 0 8px 10px rgb(84 89 219 / 0.5);
    }

   #yesBtn:hover {
      filter: brightness(1.1);
    }

  #noBtn {
      background: #ccc;
      color: #555;
      position: absolute;
      top: 50%;
      left: calc(50% + 90px);
      transform: translate(-50%, -50%);
      transition: none;
      z-index: 10;
      user-select: none;
    }

  .result {
      color: #332f6f;
    }

  .result h2 {
      font-size: 24px;
      margin-bottom: 20px;
      user-select: text;
    }

  .result img {
      max-width: 140px;
      margin: 10px 12px;
      border-radius: 12px;
      box-shadow: 0 6px 15px rgba(255, 0, 90, 0.3);
      vertical-align: middle;
    }
  </style>
</head>
<body>
  <div class="container" id="popup">
    <h1>💝 Для Самой Лучшей 💝</h1>
    <p>Будешь моей Валентинкой?</p>
    <button id="yesBtn">Да! 💞</button>
    <button id="noBtn">Нет</button>
  </div>

  <script>
    const noBtn = document.getElementById('noBtn');
    const yesBtn = document.getElementById('yesBtn');
    const popup = document.getElementById('popup');

    noBtn.addEventListener('mouseenter', () => {
      const containerRect = popup.getBoundingClientRect();
      const noBtnRect = noBtn.getBoundingClientRect();

      const maxX = containerRect.width - noBtnRect.width - 10;
      const maxY = containerRect.height - noBtnRect.height - 10;

      let newX = Math.floor(Math.random() * maxX);
      let newY = Math.floor(Math.random() * maxY);

      const yesBtnRect = yesBtn.getBoundingClientRect();
      const relativeYesX = yesBtnRect.left - containerRect.left;
      const relativeYesY = yesBtnRect.top - containerRect.top;

      if (Math.abs(newX - relativeYesX) < 50) {
        newX = (newX + 60) % maxX;
      }

      noBtn.style.left = newX + 'px';
      noBtn.style.top = newY + 'px';
    });  yesBtn.addEventListener('click', () => {
      popup.innerHTML = `
        <div class="result">
          <h2>Урааа, я так рад!</h2>
          <img src="./фото/IMG_7055.JPG" alt="Фото 1" />
          <img src="./фото/IMG_7059.JPG" alt="Фото 2" />
        </div>
      `;
    });
  </script>
</body>
</html>
