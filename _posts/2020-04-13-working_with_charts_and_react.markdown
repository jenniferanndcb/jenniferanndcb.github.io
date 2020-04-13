---
layout: post
title:      "Working with Charts and React"
date:       2020-04-13 20:16:25 +0000
permalink:  working_with_charts_and_react
---


React seems like the perfect choice of JS library to build a UI that involves a dashboard for browsing data and charts. 

**Using react-chartjs-2**

Start by installing:

```npm install react-chartjs-2 chart.js --save```

This enables a simple way to import charts into your components, as such: 

```
import {Bar} from 'react-chartjs-2';
```

**Rendering Charts**

I created a BarChart component as a simple class component which renders a canvas element which will contain the chart itself.

```
class BarChart extends React.Component {

render() {
    return (
      <div>
        <div>
          <canvas id="barChart" />
        </div>
      </div>
    );
	}
```

I gave the canvas the id="barChart" so I can easily refer to it when the barchart is instantiated within the componentDidMount(). 

```
componentDidMount() {
    this.buildChart();
  }


buildChart() {
    var ctx = document.getElementById("barChart").getContext("2d");
    barChart = new Chart(ctx, {
      type: "bar",
      data: {
        labels: ["4-5 year olds", "10-11 year olds"],
        datasets: [
          {
            label: "London",
            backgroundColor: "rgba(100, 0, 250)",
            data: {londonData}
             
          },
        ],
      },
```

The data I used to display in this chart was from an API I built with Rails. Fetched the data usung Redux (and thunk middleware) and then passed it down to the barChart component as props. 




