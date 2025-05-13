# selenium
To **install and set up Selenium in IntelliJ IDEA** for JavaScript (Node.js), follow these **step-by-step instructions slowly and clearly**:

---

### **Part 1: Install Node.js (if not installed)**

1. Go to: [https://nodejs.org](https://nodejs.org)
2. Download and install the **LTS (Long-Term Support)** version.
3. After installation, open Command Prompt and type:

```bash
node -v
npm -v
```

You should see version numbers (this means Node.js is installed).

---

### **Part 2: Install IntelliJ IDEA**

1. Download IntelliJ IDEA (Community or Ultimate) from:
   [https://www.jetbrains.com/idea/download](https://www.jetbrains.com/idea/download)
2. Install and open IntelliJ IDEA.

---

### **Part 3: Create a New Node.js Project in IntelliJ IDEA**

1. **Open IntelliJ IDEA**
2. Click on **"New Project"**
3. On the left, choose **Node.js** (if it is not visible, install the Node.js plugin: File → Settings → Plugins → search for "Node.js" and install).
4. Give your project a name (e.g., `SeleniumTest`)
5. Click **Finish**

---

### **Part 4: Initialize Node.js and Install Selenium**

Once your project opens:

1. Open the **Terminal** (bottom of IntelliJ)
2. Run these commands:

```bash
npm init -y                 # Creates package.json
npm install selenium-webdriver  # Installs Selenium WebDriver for JS
```

Now you'll see a `node_modules` folder and `package.json` file in your project.

---

### **Part 5: Write a Selenium Test Script**

1. In IntelliJ's **Project** sidebar:

   * Right-click the `src` folder (or project root)
   * Click **New → JavaScript File**
   * Name it `loginTest.js`

2. Paste this test code:

```javascript
const { Builder, By, until } = require('selenium-webdriver');

(async function testLoginForm() {
  let driver = await new Builder().forBrowser('chrome').build();

  try {
    await driver.get('http://example.com');  // Replace with your real URL

    await driver.findElement(By.name('username')).sendKeys('admin');
    await driver.findElement(By.name('password')).sendKeys('1234');
    await driver.findElement(By.css('button')).click();

    let message = await driver.wait(until.elementLocated(By.id('message')), 3000);
    let text = await message.getText();

    console.log('Test Result:', text);
  } finally {
    await driver.quit();
  }
})();
```

---

### **Part 6: Set Up ChromeDriver**

1. Download **ChromeDriver**:
   [https://sites.google.com/chromium.org/driver](https://sites.google.com/chromium.org/driver)
2. Choose the version matching your Chrome browser.
3. Extract the `chromedriver.exe` file.
4. Add the folder containing `chromedriver.exe` to your **System PATH**:

   * **Windows**: Search "Environment Variables" → Edit system variables → Add path of the folder.
5. To test if it's working, open Command Prompt and type:

```bash
chromedriver
```

You should see something like:
`Starting ChromeDriver...`

---

### **Part 7: Run the Script in IntelliJ**

1. Right-click on `loginTest.js`
2. Click **Run 'loginTest'**

You will see Chrome open automatically and the test will run!

---

Let me know if you're using a **Java project** instead of JavaScript, or if you want help with setting up tests in **Mocha** or **Jest**.
