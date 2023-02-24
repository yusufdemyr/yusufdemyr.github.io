---
layout: post
title: "Revising Aggregations - Average Population | HackerRank"
categories: [sql,code-archive]
draft: false
---
<p>Query the average population for all cities in <strong>CITY</strong>, rounded <em>down</em> to the nearest integer.</p>
    select floor(avg(population)) from city

<a href="https://www.hackerrank.com/challenges/average-population/problem?isFullScreen=true">**Problem link**</a>

<span class="Vsw2a _22j2f" aria-label="Info Icon" role="img"><svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg" class="_2ak-2" focusable="false" aria-hidden="true"><path fill-rule="evenodd" clip-rule="evenodd" d="M0 12C0 13.1046 0.895431 14 2 14H12C13.1046 14 14 13.1046 14 12V2C14 0.895431 13.1046 0 12 0H2C0.89543 0 0 0.895431 0 2V12ZM6 4C6 3.44772 6.44772 3 7 3C7.55228 3 8 3.44772 8 4C8 4.55228 7.55228 5 7 5C6.44772 5 6 4.55228 6 4ZM7.5 6C7.77614 6 8 6.22386 8 6.5V9.5C8 9.77614 8.22386 10 8.5 10C8.77614 10 9 10.2239 9 10.5C9 10.7761 8.77614 11 8.5 11H8H6H5.5C5.22386 11 5 10.7761 5 10.5C5 10.2239 5.22386 10 5.5 10C5.77614 10 6 9.77614 6 9.5V7.5C6 7.22386 5.77614 7 5.5 7C5.22386 7 5 6.77614 5 6.5C5 6.22386 5.22386 6 5.5 6H7.5Z" fill="#6055FF"></path></svg></span><text style="color:#7770ff;font-weight:600;"> Tip</text>
<ul>
    <li style="list-style: disc; color:#7770ff;">The <code>ROUND()</code> function rounds a number to a specific number of decimal places.</li>
    <li style="list-style: disc; color:#7770ff;"><code>Round(number, decimals, operation)</code>. If operation equals 0, it rounds to the nearest upper number. If operation equals 1, it rounds to the nearest lower number.</li>
    <li style="list-style: disc; color:#7770ff;">The <code>Floor()</code> function rounds to the nearest lower number.</li>
</ul>


