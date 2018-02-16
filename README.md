# mnd3inact2ed
## 2. 
```
var yScale = d3.scaleLinear().domain([0,24500]).range([0,100]);
yScale(0);
yScale(100);                                                     
yScale(24000); 
```

If we want it to set all such values to the maximum (for greater) or minimum (for lesser) range value, we need to use
the ```.clamp()``` function


```
d3.json("tweets.json",(error, data) => {dataViz(data.tweets)});
function dataViz(incomingData) {
  var nestedTweets = d3.nest().key(d => d.user).entries(incomingData);
  nestedTweets.forEach(d => {  d.numTweets = d.values.length;
})
var maxTweets = d3.max(nestedTweets, d => d.numTweets);
var yScale = d3.scaleLinear().domain([0,maxTweets]).range([0,500]);
d3.select("svg")
.selectAll("rect")
.data(nestedTweets)
.enter()
.append("rect")
.attr("width", 50)
.attr("height", d => yScale(d.numTweets))
.attr("x", (d,i) => i * 60)
.attr("y", d => 500 - yScale(d.numTweets))
.style("fill", "#FE9922")
.style("stroke", "#9A8B7A")
.style("stroke-width", "1px");}
```
