---
layout: post
title: "Draw The Triangle | HackerRank"
categories: [sql,code-archive]
permalink: /code-archive/:title/
draft: false
---

<div class="hackdown-content"><style id="MathJax_SVG_styles">.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
</style><svg style="display: none;"><defs id="MathJax_SVG_glyphs"></defs></svg><p><em>P(R)</em> represents a pattern drawn by Julia in <em>R</em> rows. The following pattern represents <em>P(5)</em>:</p>

<pre><code>* * * * * 
* * * * 
* * * 
* * 
*
</code></pre>

<p>Write a query to print the pattern <em>P(20)</em>.</p></div>


    DECLARE @i INT = 20
    WHILE (@i > 0) 
    BEGIN
        PRINT REPLICATE('* ', @i) 
        SET @i = @i - 1
    END

**Solution Is For MS SQL SERVER**

<a href="https://www.hackerrank.com/challenges/draw-the-triangle-1/problem?isFullScreen=true">**Problem link**</a>

<span class="Vsw2a _22j2f" aria-label="Info Icon" role="img"><svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg" class="_2ak-2" focusable="false" aria-hidden="true"><path fill-rule="evenodd" clip-rule="evenodd" d="M0 12C0 13.1046 0.895431 14 2 14H12C13.1046 14 14 13.1046 14 12V2C14 0.895431 13.1046 0 12 0H2C0.89543 0 0 0.895431 0 2V12ZM6 4C6 3.44772 6.44772 3 7 3C7.55228 3 8 3.44772 8 4C8 4.55228 7.55228 5 7 5C6.44772 5 6 4.55228 6 4ZM7.5 6C7.77614 6 8 6.22386 8 6.5V9.5C8 9.77614 8.22386 10 8.5 10C8.77614 10 9 10.2239 9 10.5C9 10.7761 8.77614 11 8.5 11H8H6H5.5C5.22386 11 5 10.7761 5 10.5C5 10.2239 5.22386 10 5.5 10C5.77614 10 6 9.77614 6 9.5V7.5C6 7.22386 5.77614 7 5.5 7C5.22386 7 5 6.77614 5 6.5C5 6.22386 5.22386 6 5.5 6H7.5Z" fill="#6055FF"></path></svg></span><text style="color:#7770ff;font-weight:600;"> Tip</text>
<ul>
    <li style="list-style: disc; color:#7770ff;">The INFORMATION_SCHEMA.TABLES view allows you to get information about all tables and views within a database. By default it will show you this information for every single table and view that is in the database.</li>
    <li style="list-style: disc; color:#7770ff;">Declare @(variableName) (variableType) = (desiredValue)</li>
    <li style="list-style: disc; color:#7770ff;">While @(variableName) (operation) (desiredValue)</li>
    <li style="list-style: disc; color:#7770ff;">PRINT => Returns a user-defined message to the client.</li>
    <li style="list-style: disc; color:#7770ff;">REPLICATE => Repeats a string value a specified number of times.</li>
</ul>
