---
layout: post
title: "Draw The Triangle 2 | HackerRank"
categories: [sql,code-archive]
draft: false
---
<div class="content-text challenge-text mlB hackdown-container theme-m"><div class="challenge-body-html"><div class="challenge_problem_statement"><div class="msB challenge_problem_statement_body"><div class="hackdown-content"><style id="MathJax_SVG_styles">.MathJax_SVG_Display {text-align: center; margin: 1em 0em; position: relative; display: block!important; text-indent: 0; max-width: none; max-height: none; min-width: 0; min-height: 0; width: 100%}
.MathJax_SVG .MJX-monospace {font-family: monospace}
.MathJax_SVG .MJX-sans-serif {font-family: sans-serif}
.MathJax_SVG {display: inline; font-style: normal; font-weight: normal; line-height: normal; font-size: 100%; font-size-adjust: none; text-indent: 0; text-align: left; text-transform: none; letter-spacing: normal; word-spacing: normal; word-wrap: normal; white-space: nowrap; float: none; direction: ltr; max-width: none; max-height: none; min-width: 0; min-height: 0; border: 0; padding: 0; margin: 0}
.MathJax_SVG * {transition: none; -webkit-transition: none; -moz-transition: none; -ms-transition: none; -o-transition: none}
.mjx-svg-href {fill: blue; stroke: blue}
</style><svg style="display: none;"><defs id="MathJax_SVG_glyphs"></defs></svg><p><em>P(R)</em> represents a pattern drawn by Julia in <em>R</em> rows. The following pattern represents <em>P(5)</em>:</p>

<pre><code>* 
* * 
* * * 
* * * * 
* * * * *
</code></pre>

<p>Write a query to print the pattern <em>P(20)</em>.</p></div></div></div></div></div>


    Declare @i int = 1
    while (@i < 21)
    begin
        print replicate('* ',@i)
        set @i = @i + 1
    end

<a href="https://www.hackerrank.com/challenges/draw-the-triangle-2/problem?isFullScreen=true">**Problem link**</a> 