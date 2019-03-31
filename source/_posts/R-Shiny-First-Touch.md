---
title: R Shiny First Touch
tags: [R Shiny]
categories: [Coding, R]
---

>This is the first time that I experience building Shiny App.
![](https://i.imgur.com/IZB6sWk.png)
<!-- more -->
## Hosting Dynamic Sites Here Are Like Dreams

One problem I just realize, is that GitHub Pages is a static site host!  
The only way to showcase my little work is by the HTML iframe.  
Better than noting tho :D  
<iframe width="900" height="750" src="https://safersky.shinyapps.io/shiny-climatechange/" frameborder="0" allowfullscreen></iframe>

## Side Note
There are plenty of things I can improve.  
Notice that I only pulled the Vancouver average Snow and Temperature measures from the database.  
I can make a drop-down menu for users to choose a specific Province/City, then use `grep` to filter a sub data frame for that.  
Also, users should be able to switch to some other databases of their choices, like the Canada Min/Max Temperature database.  
I will be updating this Shiny App, if I have time...  

If you are interested, feel free to get the code and all the data tables from my [repo](https://github.com/SaferSky/Shiny-ClimateChange).