---
layout: post
title: "Population Census | HackerRank"
categories: [sql,code-archive]
draft: false
---
<div class="hackdown-content"><style id="MathJax_SVG_styles">.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
</style><svg style="display: none;"><defs id="MathJax_SVG_glyphs"></defs></svg><p>Given the <strong>CITY</strong> and <strong>COUNTRY</strong> tables, query the sum of the populations of all cities where the <em>CONTINENT</em> is <em>'Asia'</em>.</p>

<p><strong>Note:</strong> <em>CITY.CountryCode</em> and <em>COUNTRY.Code</em> are matching key columns.</p></div>
    select sum(city.population) from city ,country 
        where city.countrycode = country.code and country.continent = 'Asia'

<a href="https://www.hackerrank.com/challenges/asian-population/problem?isFullScreen=true">**Problem link**</a> 