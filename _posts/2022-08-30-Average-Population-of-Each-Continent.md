---
layout: post
title: "Average Population of Each Continent | HackerRank"
categories: [sql,code-archive]
draft: false
---
<div class="hackdown-content"><style id="MathJax_SVG_styles">.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
.MathJax_SVG_LineBox {display: table!important}
.MathJax_SVG_LineBox span {display: table-cell!important; width: 10000em!important; min-width: 0; max-width: none; padding: 0; border: 0; margin: 0}
</style><svg style="display: none;"><defs id="MathJax_SVG_glyphs"></defs></svg><p>Given the <strong>CITY</strong> and <strong>COUNTRY</strong> tables, query the names of all the continents (<em>COUNTRY.Continent</em>) and their respective average city populations (<em>CITY.Population</em>) rounded <em>down</em> to the nearest integer.</p>

<p><strong>Note:</strong> <em>CITY.CountryCode</em> and <em>COUNTRY.Code</em> are matching key columns.</p></div>


    select country.continent,floor(avg(city.population)) from city, country 
        where city.countrycode = country.code group by country.continent

<a href="https://www.hackerrank.com/challenges/average-population-of-each-continent/problem?isFullScreen=true">**Problem link**</a> 