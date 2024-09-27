# DigitalClock

![image](https://github.com/user-attachments/assets/eb1a620a-6985-4540-a561-b7632ca53290)

### Digital Clock Documentation

This HTML document creates a live, responsive digital clock that displays the current time in a 12-hour format (AM/PM) and refreshes every second.

---

### HTML Structure:

1. **Basic HTML Setup**:
    - The document is structured using standard HTML5 with the `<!DOCTYPE html>` declaration.
    - The `<meta charset="UTF-8">` ensures the page displays characters correctly.
    - The `meta name="viewport"` tag ensures proper scaling and responsiveness for different device screen sizes.
    - The `<title>` defines the document’s title, "Digital Clock".

2. **Body Section**:
    - Inside the `<body>` tag, there is a single `<div>` with the class `.container`, which contains another `<div>` with the class `.clock`. This is where the digital clock will be displayed.

---

### CSS (Style):

1. **Body Styling**:
    - **`background-color: #333;`**: The body has a dark background (`#333`).
    - **`color: #fff;`**: Text color is white.
    - **`padding-top: 100px;`**: Padding at the top gives space before the clock is displayed.

2. **Container Styling (`.container`)**:
    - The `.container` class uses `display: flex; justify-content: center;` to horizontally center the clock within the viewport.

3. **Clock Styling (`.clock`)**:
    - **`font-size: 2em;`**: The default font size for the clock is set to `2em`.
    - A media query increases the font size to `3em` for screens wider than 600px for better visibility on larger devices.

4. **Span Styling**:
    - **`background-color: #111;`**: Each span inside the clock has a darker background color (`#111`).
    - **`border-radius: 10px;`**: Rounded corners are applied to the background of each time unit.
    - **`color: #fff;`**: The text within each span remains white.
    - **`display: inline-block;`**: Each time unit is displayed inline with padding and margin around them.
    - **`padding: .5em; margin: .2em 0;`**: Spacing is added around the time values for better readability.

---

### JavaScript (Script):

1. **Selecting the Clock Element**:
    ```javascript
    const clock = document.querySelector('.clock');
    ```
    - The `document.querySelector('.clock')` selects the HTML element with the class `clock` and stores it in the `clock` constant.

2. **Tick Function**:
    ```javascript
    const tick = () => {
        const now = new Date();
        let h = now.getHours();
        const m = now.getMinutes();
        const s = now.getSeconds();
        let am_pm = 'AM';
    ```
    - The `tick` function is used to get the current time using JavaScript's `Date` object.
    - The `getHours()`, `getMinutes()`, and `getSeconds()` methods retrieve the current hour, minute, and second values, respectively.
    - The `am_pm` variable is initialized as 'AM' by default.

3. **12-Hour Format Conversion**:
    ```javascript
    if (h >= 12) {
        h -= 12; 
        am_pm = "PM";
    }
    if (h == 0) {
        h = 12;
        am_pm = "AM";
    }
    ```
    - To convert the 24-hour clock to a 12-hour format:
        - If the hour (`h`) is greater than or equal to 12, 12 is subtracted from it, and the `am_pm` is set to "PM".
        - If the hour is `0` (midnight), it is set to 12 to represent 12 AM.

4. **HTML Structure of the Clock**:
    ```javascript
    const html = `
      <span>${h}</span> : 
      <span>${m}</span> : 
      <span>${s}</span> 
      <span class="ampm">${am_pm}</span>
    `;
    ```
    - The clock time is dynamically inserted into the HTML. Each component (hour, minute, second, AM/PM) is wrapped in a `<span>` element to apply individual styling.

5. **Updating the Clock**:
    ```javascript
    clock.innerHTML = html;
    ```
    - The generated HTML from the `html` variable is injected into the `.clock` div using `innerHTML`.

6. **Auto-Refreshing the Clock**:
    ```javascript
    setInterval(tick, 1000);
    ```
    - The `setInterval()` method calls the `tick()` function every 1000 milliseconds (1 second), refreshing the time on the screen.

---

### Summary of Interaction:

1. The **`tick()`** function is responsible for obtaining the current time, converting it to 12-hour format, and formatting it as HTML.
2. Every second, the **`setInterval()`** function refreshes the time displayed in the `.clock` div.
3. The clock updates dynamically in real-time, displaying the hours, minutes, seconds, and AM/PM indicator.

This code results in a responsive, easy-to-read digital clock that functions across different devices. The styling ensures good contrast between the clock and the background, and the JavaScript handles live time updates.
