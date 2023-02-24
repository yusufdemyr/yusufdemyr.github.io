---
layout: post
title: "Type of Triangle | HackerRank"
categories: [sql,code-archive]
draft: false
---
What i learned from this problem: **Nested if structure in MySQL.**

<a href="https://www.hackerrank.com/challenges/what-type-of-triangle/problem?isFullScreen=true">**Problem link**</a> 

    /*
    Enter your query here.
    */
    Select 
        if((a+b <= c),"Not A Triangle",
            if((a=b and b=c and c=a),"Equilateral",
                if((a=b or a=c or b=c),"Isosceles",
                    if((a!=b and b!=c and a!=c),"Scalene","")))) 
        From Triangles;