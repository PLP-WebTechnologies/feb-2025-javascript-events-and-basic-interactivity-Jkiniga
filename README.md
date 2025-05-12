# 🎯 JavaScript Event Handling & Interactive Elements Assignment

Welcome to the **ultimate JavaScript playground**! 🎉 This assignment is where we turn boring web pages into dynamic, responsive, *alive* experiences. Get ready to master **event handling**, build **interactive components**, and validate forms like a pro! 💪

## 📁 Assignment Structure

```
📂 js-event-assignment/
├── index.html         # Your playground – where it all comes together
├── style.css          # Keep it cute (optional but encouraged)
└── script.js          # The JavaScript wizardry happens here
```

---

## 🧪 What to Build

Here’s what your interactive bundle of joy should include:

### 1. Event Handling 🎈  
- Button click ✅  
- Hover effects ✅  
- Keypress detection ✅  
- Bonus: A secret action for a *double-click* or *long press* 🤫

### 2. Interactive Elements 🎮  
- A button that changes text or color  
- An image gallery or slideshow  
- Tabs or accordion-style content  
- Bonus: Add some animation using JS or CSS ✨

### 3. Form Validation 📋✅  
- Required field checks  
- Email format validation  
- Password rules (e.g., min 8 characters)  
- Bonus: Real-time feedback while typing

---

## 🧙‍♂️ Pro Tips

- Keep your code clean and commented – your future self will thank you!
- Think about **user experience** – what makes your site more *fun* to use?
- Don’t be afraid to **Google and experiment** – that’s how real developers roll!

---

## 🎉 Now Go Make It Fun!

Remember – this isn't just code. It's your **first step toward creating magical user experiences**. So play around, break stuff (then fix it), and most of all, have FUN! 😄

Happy Coding! 💻✨  
<!-- index.html -->
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta http-equiv="X-UA-Compatible" content="IE=edge" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>JS Event Assignment</title>
  <link rel="stylesheet" href="style.css" />
</head>
<body>
  <h1>JS Event Assignment Playground</h1>

  <!-- 1. Event Handling -->
  <section id="events">
    <button id="clickBtn">Click me</button>
    <div id="hoverBox">Hover over me</div>
    <input id="keyInput" placeholder="Type something..." />
    <!-- Bonus: double-click or long press -->
    <button id="secretBtn">Secret Action</button>
  </section>

  <!-- 2. Interactive Elements -->
  <section id="interactive">
    <button id="colorBtn">Change my color/text</button>
    <div id="gallery">
      <img src="https://via.placeholder.com/150?text=1" class="thumb" data-index="0">
      <img src="https://via.placeholder.com/150?text=2" class="thumb" data-index="1">
      <img src="https://via.placeholder.com/150?text=3" class="thumb" data-index="2">
    </div>
    <div id="galleryDisplay">
      <img src="https://via.placeholder.com/300?text=1" id="mainImg">
    </div>
    <div class="tabs">
      <button class="tabBtn" data-tab="tab1">Tab 1</button>
      <button class="tabBtn" data-tab="tab2">Tab 2</button>
    </div>
    <div class="tabContent" id="tab1">Content for Tab 1</div>
    <div class="tabContent" id="tab2">Content for Tab 2</div>
  </section>

  <!-- 3. Form Validation -->
  <section id="formSection">
    <form id="signupForm">
      <label>
        Name (required): <input type="text" id="name">
      </label><br>
      <label>
        Email (required): <input type="email" id="email">
      </label><br>
      <label>
        Password (min 8 chars): <input type="password" id="password">
      </label><br>
      <button type="submit">Submit</button>
    </form>
    <div id="formErrors"></div>
  </section>

  <script src="script.js"></script>
</body>
</html>

/* style.css */
/* Optional styling to make it look cute */
body {
  font-family: Arial, sans-serif;
  margin: 2rem;
}
#hoverBox {
  width: 200px;
  height: 50px;
  background: lightgray;
  line-height: 50px;
  text-align: center;
  margin-top: 1rem;
}
#interactive img {
  cursor: pointer;
  margin: 0.5rem;
}
.tabs {
  margin-top: 1rem;
}
.tabContent {
  display: none;
  margin-top: 0.5rem;
}
.tabContent.active {
  display: block;
}
#formErrors {
  color: red;
  margin-top: 0.5rem;
}

// script.js
// 1. Event Handling
const clickBtn = document.getElementById('clickBtn');
const hoverBox = document.getElementById('hoverBox');
const keyInput = document.getElementById('keyInput');
const secretBtn = document.getElementById('secretBtn');

clickBtn.addEventListener('click', () => {
  alert('Button clicked!');
});

hoverBox.addEventListener('mouseover', () => {
  hoverBox.style.background = 'lightblue';
});
hoverBox.addEventListener('mouseout', () => {
  hoverBox.style.background = 'lightgray';
});

keyInput.addEventListener('keypress', (e) => {
  console.log(`Key pressed: ${e.key}`);
});

// Bonus: double-click secret action
secretBtn.addEventListener('dblclick', () => {
  alert('🤫 Secret unlocked!');
});

// 2. Interactive Elements
const colorBtn = document.getElementById('colorBtn');
colorBtn.addEventListener('click', () => {
  colorBtn.textContent = 'Clicked!';
  colorBtn.style.background = '#ffc107';
});

// Gallery/Slideshow
const thumbs = document.querySelectorAll('.thumb');
const mainImg = document.getElementById('mainImg');
thumbs.forEach(img => {
  img.addEventListener('click', () => {
    const idx = img.dataset.index;
    mainImg.src = `https://via.placeholder.com/300?text=${parseInt(idx)+1}`;
  });
});

// Tabs
const tabBtns = document.querySelectorAll('.tabBtn');
const tabContents = document.querySelectorAll('.tabContent');

function deactivateTabs() {
  tabBtns.forEach(b => b.classList.remove('active'));
  tabContents.forEach(c => c.classList.remove('active'));
}

tabBtns.forEach(btn => {
  btn.addEventListener('click', () => {
    deactivateTabs();
    btn.classList.add('active');
    document.getElementById(btn.dataset.tab).classList.add('active');
  });
});

// Activate first tab by default
tabBtns[0].click();

// 3. Form Validation
const form = document.getElementById('signupForm');
const errorsDiv = document.getElementById('formErrors');

form.addEventListener('submit', (e) => {
  e.preventDefault();
  errorsDiv.textContent = '';
  const name = document.getElementById('name').value.trim();
  const email = document.getElementById('email').value.trim();
  const password = document.getElementById('password').value;
  const errors = [];

  if (!name) errors.push('Name is required.');
  if (!email || !/^\S+@\S+\.\S+$/.test(email)) errors.push('Valid email is required.');
  if (password.length < 8) errors.push('Password must be at least 8 characters.');

  if (errors.length) {
    errorsDiv.innerHTML = errors.map(err => `<div>${err}</div>`).join('');
  } else {
    alert('Form submitted successfully!');
    form.reset();
  }
});
