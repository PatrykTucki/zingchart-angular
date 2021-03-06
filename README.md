# zingchart-angular

Quickly add charts to your Angular application with our ZingChart component

# 1. Install
Install the zingchart-angular package via npm

$ npm install zingchart-angular

# 2. Include the component in your project

Include the module in your module declaration file.

`import { ZingchartAngularModule } from 'zingchart-angular';`

```
@NgModule({
  imports: [
    ...
    ZingchartAngularModule,
  ],
})
```

# 3. Define your chart configuration in your component.

```
config:zingchart.graphset = {
  type: 'line',
  series: [{
    values: [3,6,4,6,4,6,4,6]
  }],
};
```

# 4. Add your component to the markup.

```
  <zingchart-angular [config]="config" [height]="500"></zingchart-angular>
```

## Parameters

### config [object]
The chart configuration (graphset)

```
config:zingchart.graphset = {
  type: 'line',
  series: [{
    values: [3,6,4,6,4,6,4,6]
  }],
};

<zingchart-angular [config]="config" [height]="500"></zingchart-angular>
```

### id [string] (optional)

The id for the DOM element for ZingChart to attach to. If no id is specified, the id will be autogenerated in the form of zingchart-angular-#

### series [array] (optional)

Accepts an array of series objects, and overrides a series if it was supplied into the config object. Varries by chart type used - Refer to the ZingChart documentation for more details.

```
  series:zingchart.series = {
    values: [3,6,4,6,4,6,4,6]
  }
  config:zingchart.graphset = {
    type: 'line',
    series: [this.series]
  };
    <zingchart-angular [config]="config" [height]="500" [series] = "[series]"></zingchart-angular>
```

### width [string or number] (optional)
The width of the chart. Defaults to 100%

### height [string or number] (optional)
The height of the chart. Defaults to 480px.

### theme [object] (optional)
The theme or 'defaults' object defined by ZingChart. More information available here: https://www.zingchart.com/docs/api/themes

## Events
All zingchart events are readily available on the component to listen to. For example, to listen for the 'complete' event when the chart is finished rendering:

```
  <zingchart-angular[config]="config" [height]="300" (complete)="onComplete($event)"></zingchart-angular>

  export class AppComponent {
      ...
    onComplete(ev) {
      console.log('on complete!');
    }
  }
```

## Methods

All zingchart methods are readily available on the component's instance to call. For example, to retrieve data from the chart,

```
  <zingchart-angular #chart1 [config]="config"></zingchart-angular>

    export class AppComponent {
      ...

    obtainData() {
      return this.chart.getdata();
    }

  }

```
