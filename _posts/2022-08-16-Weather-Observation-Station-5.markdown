---
layout: post
title: "Weather Observation Station 5 | HackerRank"
categories: [sql,code-archive]
draft: false
---

What i learned from this problem: 
<ul>
<li>You can't use len function in MySQL. You should use length() function instead of len().</li>
<li>Also you can order by columns seperately.</li>
</ul>
Note that you can write seperate queries to get the desired output.


<a href="https://www.hackerrank.com/challenges/weather-observation-station-5/problem?isFullScreen=true">**Problem link**</a> 

    /*
    Enter your query here.
    */

    select city , length(city) from station where city = 
                (select city from station order by length(city), city ASC limit 1);
    select city , length(city) from station where city = 
                (select city from station order by length(city) DESC,city ASC limit 1);

<li>First query is selecting first row as well as ordering ascending and alphabetical order by city and length of city.</li>
<li>Second query is selecting first row as well as ordering descending order by length of city but also ordering by alphabetical order by city.</li>
