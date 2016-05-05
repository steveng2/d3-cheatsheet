# D3.js Cheatsheet

## d3.js quick reference sheet

### Table of contents
- [Attributes/Styles](#attributesstyles)
- [Properties](#properties)
- [Axis](#axis)
- [Time parsing/formatting](#time-parsingformatting)
- [Color](#color)

### Attributes/Styles
#### Attributes/Styles - initialization
```javascript
var svgWrapper = d3.select("body")
  .append("svg")
  .attr("id", "viz")
  .attr("width", width + margin.left + margin.right)
  .attr("height", height + margin.top + margin.bottom);

var container = svgWrapper.append("g")
  .attr("transform", "translate(" + margin.left + "," + margin.top + ")")
  .style("pointer-events", "all");
```

#### Attributes/Styles - circle
```javascript
this.attr("r", style.r)
  .attr("fill", style.fill)
  .attr("stroke", style.color)
  .attr("stroke-width", style["stroke-width"])
```

### Properties
```javascript
var id = d3.select("#id").property("value");
d3.select("input").property("value", d3.event.keyCode);
```

### Axis
```javascript
var xAxis = d3.svg.axis()
  .scale(_xScale)
  .orient("bottom")
  .ticks(4)
  .tickFormat(d3.time.format('%d %b %I%p')) //14 Feb 12AM
  .tickSize(5);
```

### Time parsing/formatting
```javascript
var parseDate = d3.time.format("%Y-%m-%dT%H:%M:%SZ").parse,
  formatDate = d3.time.format("%d %b %H:%M:%S"),
  formatDateForQuery = d3.time.format("%Y-%m-%dT%H:%M:%SZ"),
  formatTime = d3.time.format("%H:%M:%S");
```
### Color
#### Custom color ordinal scale
```javascript
var myCategory20Colors = [
  0x1f77b4, 0xaec7e8,
  0xff7f0e, 0xffbb78,
  0x2ca02c, 0x98df8a,
  0xd62728, 0xff9896,
  0x9467bd, 0xc5b0d5,
  0x8c564b, 0xc49c94,
  0xe377c2, 0xf7b6d2,
  0xbcbd22, 0xdbdb8d,
  0x17becf, 0x9edae5
].map(function(x) {
    var value = x + "";
    return d3.rgb(value >> 16, value >> 8 & 0xff, value & 0xff).toString();
});

var myCategory20 = d3.scale.ordinal().range(myCategory20Colors);
console.log(myCategory20("x"), myCategory20("y"));
// #1f77b4 #aec7e8
```javascript
