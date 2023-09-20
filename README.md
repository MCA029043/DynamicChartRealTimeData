# Dynamic chart Real-Time Data

This is a simple real-time chart implemented using Chart.js. The chart displays randomly generated data points that update every second. You can customize the line color and hover over data points to see their values.

### Prerequisites

To run this project, you will need the following:

- Node.js installed on your system
- A code editor such as Visual Studio Code

### Setup

1. Clone this repository to your local machine.
2. Install the dependencies by running `npm install`.
3. Start the server by running `npm start`.

### Usage

The chart will automatically start updating in real time. You can change the data that is being plotted by editing the `data` array in the `index.js` file.

### Code Explanation

The code for this project is relatively simple. Let's go through it step by step.

#### HTML

The HTML file for this project is very simple. It just includes the necessary HTML elements and links to the JavaScript and CSS files.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Dynamic chart Real-Time Data</title>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="stylesheet" href="style.css" />
  </head>
  <body>
    <div id="div">
      <canvas id="realTimeChart"></canvas>
    </div>
    <input type="color" id="lineColor" value="#4bdcff">
    <label for="lineColor">Choose Color</label>
    <script src="index.js"></script>
  </body>
</html>
```

#### CSS

The CSS file for this project is also very simple. It just sets the width and height of the chart.

```css
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  canvas {
    max-width: 100%;
    height: auto;
  }
  #div {
    width: 80%;
    margin: auto;
  }
  #lineColor{
    margin-left: 10%;
    margin-top: 25px;
  }
```

#### JavaScript

The JavaScript file for this project is where the magic happens. This is where we create the chart and update it in real time.

```javascript
const ctx = document.getElementById("realTimeChart").getContext("2d");
let chart;
const initialData = {
  labels: [],
  datasets: [
    {
      label: "Value",
      data: [],
      borderColor: "rgba(75, 192, 192, 1)",
      borderWidth: 1,
      fill: false,
    },
  ],
};
const chartConfig = {
  type: "line",
  data: initialData,
  options: {
    scales: {
      x: {
        type: "linear",
        position: "bottom",
        title: {
          display: true,
          text: "Time",
        },
      },
      y: {
        beginAtZero: true,
        title: {
          display: true,
          text: "Value",
        },
      },
    },
    animation: false,
  },
};
chart = new Chart(ctx, chartConfig);
function addData() {
  const newData = Math.random() * 500;
  chart.data.labels.push(chart.data.labels.length);
  chart.data.datasets[0].data.push(newData);
  chart.update();
}
setInterval(addData, 1000);




  function addData() {
    const newData = Math.random() * 500;
    const lineColor = document.getElementById("lineColor").value;

    chart.data.labels.push(chart.data.labels.length);
    chart.data.datasets[0].data.push(newData);
    chart.data.datasets[0].borderColor = lineColor;
    chart.update();
  }


```
