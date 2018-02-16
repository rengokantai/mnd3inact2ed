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
