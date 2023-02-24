---
layout: post
draft: true
title: "Liquid Template Language"
categories: language
description: "This page a guideline to Liquid Template Language for personal reasons"
variable: {
  value: 'test',
  value2: 'test2',
  value3: 'test3'
}
about-us: "A"
settings: {
  featured_potions_title: "Health Potion"
}
recipes: empty
---
<style>
  *{font-size: 17px;}
    .red {color: red}
    .btn{ width: 170px;
       height: 40px;
      
       color:blue;
       border: 2px solid #000;
       font-family: 'Lato', sans-serif;
       font-weight: 500;
       background: transparent;
       cursor: pointer;
       transition: all 0.3s ease;
       position: relative;
       display: inline-block;
       
       line-height: 39px; 
       padding: 0;
    }
    li{
      list-style:none;
    }
    #mylist > li{
      list-style:disc;
    }
    table {
      font-family: arial, sans-serif;
      border-collapse: collapse;
      width: 100%;
    }

    td, th {
      border: 1px solid #dddddd;
      text-align: left;
      padding: 8px;
    }

    tr:nth-child(even) {
      background-color: #dddddd;
    }
    .btn:hover{background: transparent;color: #000;text-decoration: none !important;}
    .btn span{position: relative;
       display: block;
       width: 100%;
       height: 100%;}
    .btn:before,
    .btn:after {
      position: absolute;
      content: "";
      left: 0;
      top: 0;
      background: #000;
      transition: all 0.3s ease;
    }
    .btn:before {
      height: 0%;
      width: 2px;
    }
    .btn:after {
      width: 0%;
      height: 2px;
    }
    .btn:hover:before {
      height: 100%;
    }
    .btn:hover:after {
      width: 100%;
    }
    .btn span:before,
    .btn span:after {
      position: absolute;
      content: "";
      right: 0;
      bottom: 0;
      background: #000;
      transition: all 0.3s ease;
    }
    .note-up{
      
      display: flex;
      width: 100%;
      height: 10%;
      border-top: 1px solid black;
      border-bottom: 1px solid black;
      justify-content: center;
      font-weight:600;

    }

    .btn span:before {
      width: 2px;
      height: 0%;
    }
    .btn span:after {
      width: 0%;
      height: 2px;
    }
    .btn span:hover:before {
      height: 100%;
    }
    .btn span:hover:after {
      width: 100%;
    }
   hr{
    border-top: 1px solid black;
   }

</style>

<img src="../assets/border-pattern.png" alt="pattern" width="250" height="40">
<a class="btn" href="https://shopify.dev/api/liquid">you can find source here</a>
<img src="../assets/border-pattern.png" alt="pattern" width="250" height="40">


### **What is a template language?**
<li> A template language allows you to create a single template to host static content, and dynamically insert information depending on where the template is rendered.</li>
<li> For example, you can create a product template that hosts all of your standart product attributes, such as the product image, title, and price.</li>
<li> That template can then dynamically render those attributes with the appropriate content, depending on the current product being viewed.</li>

### **Liquid Basics**
<li> Liquid is used to dynamically output objects and their properties. You can further modify that output by creating logic with tags, or directly altering it with a filter. Objects and objects properties are output using one of six basic data types. Liquid also includes basic logical and comparison operators for use with tags.</li>

{% raw %}
```html
<title>
  {{ page.title }}
</title>
{% if page.description %}
  <meta name="description" content="{{ page.description | escape }}">
{% endif %}
```
{% endraw %}
<b>page.title</b> -> Using the codes you defined at the beginning of the page, the title assigned to the page shows the variable owned by the title.<br>
<b>page.description</b> -> Using the codes you defined at the beginning of the page, the description assigned to the page shows its variable.<br>
<b>{% raw %} {% if .. %} {% endraw %}</b> -> That means like if true run that code block.<br>
<code>
OUTPUT<br>
{{page.title}}<br>
{% if page.description %}
    <meta name="description" content="{{page.description | escape}}">
{% endif %}
<a class="btn" href="#basics">Navigate to Basics</a>

### **Defining logic with tags**
<li>Liquid tags are used to define logic that tells templates what to do. Text within tag delimiters doesn't produce visible output when the webpage is rendered.</li>
<code>{% raw %} {% %} {% endraw %} -> Curly brace percentage delimiters denote logic and control flow.</code>
    {% raw %}
    {% if product.title == 'Health potion' %}
    This is a rare potion. Use it sparingly!
    {% endif %}
    {% else %}
    This is not a rare potion. Trash!
    {% endraw %}
So the output is:
    {% assign my_variable = "Health Potion" %}
    {% if product.title == 'Health Potion' %}
    This is a rare potion. Use it sparingly!
    {% else %}
    This is not a rare potion. Trash!
    {% endif %}
<a class="btn" href="#tags">Navigate to Tags</a>

### **Modifying output with filters**
<li> Liquid filters are used to modify the output of variables and objects. To apply filters to an output, add the filter and any filter parameters within the output's curly brace delimiters, preceded by a pipe character.</li>
<li> Multiple filters can be used on one output. They're parsed from left to right.</li><br>
<code><b>{% raw %}{{ | }}{% endraw %} -></b> Filters are placed within an output tag and denoted by a pipe character.</code>
    {% raw %}
    {% assign my_variable = "Health Potion" %}
    {{ my_variable | upcase | remove: 'HEALTH' }}
    {% endraw %}
Output:
    {% assign my_variable = "Health Potion" %}
    {{ my_variable | upcase | remove: 'HEALTH' }}

<a class="btn" href="#filters">Navigate to Filters</a>

### **Referencing objects**


<li>Liquid objects represent variables that you can use to build your theme. Object types include, but aren't limited to:</li>
<ul id="mylist">
<li>Store resources, such as a collection or product and its properties</li>
<li>Standart content that is used to power Shopify themes, such as <code>content_for_header</code></li>
<li>Functional elements that can be used to build interactivity, such as <code>paginate</code> and <code>search</code></li>
<li>Objects might represent a single data point, or contain multiple properties. Some products might represent a related object, such as a product in collection</li>
<code><b>{% raw %}{{  }}{% endraw %} -></b> Double curly brace delimiters denote an output.</code>
</ul>

{% raw %}
```html
  <div class=”product-page”>
      <div class=”product-image”>
        {{ product.featured_image | image_url: width: 400 | image_tag }}
      </div>
    <div class=”product-title”>
      {{ product.title }}
    </div>
    <div class=”product-price”>
      {{ product.price | money }}
    </div>
  </div>
```
{% endraw %}

Output:
```html
<div class=”product-page”>
  <div class=”product-image”>
    <img src="//cdn.shopify.com/s/files/1/0561/7470/6753/products/science-beakers-blue-light.jpg?v=1654828801&amp;width=400" alt="Health potion" srcset="//cdn.shopify.com/s/files/1/0561/7470/6753/products/science-beakers-blue-light.jpg?v=1654828801&amp;width=352 352w" width="400" height="267">
  </div>
  <div class=”product-title”>
    Health potion
  </div>
  <div class=”product-price”>
    $10.00
  </div>
</div>
```
#### **Scope**
<li>Some objects can be accessed globally, and some are available only in certain contexts. Refer to the specific object reference to find its access scope.</li>

#### **Creating variables**
<li>You can also create your own variables using variable tags. Variables are treated like objects syntactically.</li>
<br>
<a class="btn" href="#objects">Navigate to Objects</a>

<span id="basics">

## **Basics**
### **Object handles**
<li>Object that represent store resources, such as products, collections, article, and blogs, have handles for identifying an individual resource. The handle is used to build the URL for that resource, or to return properties for the resource.</li>
<li>Other objects like <code>linklists</code>,<code>links</code>, and <code>settings</code> also have handles.</li>

#### **Creating and modifying handles**

<li>Handles are automatically generated based on the resource title. They follow a set of rules: </li>
<ul id="mylist">
<li>Handles are always lowercase</li>
<li>whitespace and special characters are replaced with a hyphen <code>-</code>.</li>
<li>If there are multiple consecutive whitespace or special characters, then they're replaced with a single hyphen.</li>
<li>Whitespace or special characters at the beginning are removed.</li>
</ul>
<li>Handles need to be unique, so if a dublicate title is used, then the handle is auto-incremented by one. For example, if you had two products called <code>Potion</code>, then their handles would be <code>potion</code> and <code>potion-1</code>.</li>
<li>After a resouce has been created, changing the resource title doesn't update the handle.</li>

<span class="note-up">★·.·´¯\`·.·★ ɴᴏᴛᴇ★·.·´¯\`·.·★</span>
Individual links from <code>linklists</code> have  handles based on their titles. These handles can't be modified directly. Individual settings, from <code>settings_schema.json</code>, sections, or blocks, get their handle from their <code>id</code> property.
<hr/>

  {% raw %}
    {{ page.title | handle }}
  {% endraw %}
Output =
  {{page.title | handle }}

#### **Referencing handles**

All objects that have a <code>handle</code> property. For example, you can output a product's handle with <code>product.handle</code>. You can reference an object, from within its parent object, by its handle in two ways:
<ul id="mylist">
<li>Square bracket notation <code>[ ]</code>: Accepts a handle wrapped in quotes <code>'</code>, a Liquid variable, or an object reference.</li>
<li>Dot notation <code>.</code>: Accepts a handle without quotes.</li>
</ul>
<span class="note-up">★·.·´¯\`·.·★ ɴᴏᴛᴇ★·.·´¯\`·.·★</span>
Referencing an object by its handle is similar to <a href="#types">referencing array elements by their index.</a>
<hr/>

  {% raw %}
    'About us' page URL: {{ page['variable'].value }}
    Enable product suggestions: {{ settings.predictive_search_enabled }}
  {% endraw %}
Output =
<div></div>
    'Variable' page value: {{ page['variable'].value }}
    'Variable' page value2: {{ page['variable'].value2 }}

<span id="#operators">
### **Logical and comparison operators**
<li>Liquid supports basic logical and comparison operators for use with <a href="#tags">conditional tags.</a></li>
<br>
<table>
<tr>
  <th>Operator</th>
  <th>Function</th>
</tr>
<tr>
  <td>==</td>
  <td>equals</td>
</tr>
<tr>
  <td>!=</td>
  <td>does not equal</td>
</tr>
<tr>
  <td>></td>
  <td>greater than</td>
</tr>
<tr>
  <td><</td>
  <td>less than</td>
</tr>
<tr>
  <td>>=</td>
  <td>greater than or equal to</td>
</tr>
<tr>
  <td><=</td>
  <td>less than or equal to</td>
</tr>
<tr>
  <td>or</td>
  <td>Condition A or Condition B</td>
</tr>
<tr>
  <td>and</td>
  <td>Condition A and Condition B</td>
</tr>
<tr>
  <td>contains</td>
  <td>Checks for strings in strings or arrays</td>
</tr>
</table>

####  ***contains***
<li>You can use <code>contains</code> to check for the presence of a string within an array, or another string. You can't use <code>contains</code> to check for an object in an array of objects.</li>

  {% raw %}
    {% if page.variable contains 'value3' %}
      This potion contains restorative properties.
    {% endif %}
  {% endraw %}
Output = 

<div></div>
  {% if page.variable contains 'value3' %}
    This potion contains restorative properties.
  {% else %}
    Fuck You
  {% endif %}
if contains key not key value.

####  **Order of operations**
When using more than one operator in a tag, the operators are evaluated from right to left, and you can't change this order.
<li style='color:#ebaf26;list-style: none; font-size:20px;font-weight:600'>**Caution**</li>
<li style = 'color:#ebaf26;'>Parentheses<code>()</code> aren't valid characters within Liquid tags. If you try to include them to group operators, then your tag won't be rendered.</li>
  {% raw %}
    {% unless true and false and false or true %}
      This evaluates to false, since Liquid checks tags like this:

      true and (false and (false or true))
      true and (false and true)
      true and false
      false
    {% endunless %}
  {% endraw %}
Output =
<div></div>
  {% unless true and false and false or true %}
    This evaluates to false, since Liquid checks tags like this:

      true and (false and (false or true))
      true and (false and true)
      true and false
      false
  {% endunless %}

  
<span id="#types">
### **Types**
<li>Liquid output can be one of six data types.</li>
#### **string**
<li>Any series of characters, wrapped in sinle or double quotes.</li>
<span class="Vsw2a _22j2f" aria-label="Info Icon" role="img"><svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg" class="_2ak-2" focusable="false" aria-hidden="true"><path fill-rule="evenodd" clip-rule="evenodd" d="M0 12C0 13.1046 0.895431 14 2 14H12C13.1046 14 14 13.1046 14 12V2C14 0.895431 13.1046 0 12 0H2C0.89543 0 0 0.895431 0 2V12ZM6 4C6 3.44772 6.44772 3 7 3C7.55228 3 8 3.44772 8 4C8 4.55228 7.55228 5 7 5C6.44772 5 6 4.55228 6 4ZM7.5 6C7.77614 6 8 6.22386 8 6.5V9.5C8 9.77614 8.22386 10 8.5 10C8.77614 10 9 10.2239 9 10.5C9 10.7761 8.77614 11 8.5 11H8H6H5.5C5.22386 11 5 10.7761 5 10.5C5 10.2239 5.22386 10 5.5 10C5.77614 10 6 9.77614 6 9.5V7.5C6 7.22386 5.77614 7 5.5 7C5.22386 7 5 6.77614 5 6.5C5 6.22386 5.22386 6 5.5 6H7.5Z" fill="#6055FF"></path></svg></span><text style="color:#7770ff;font-weight:600;"> Tip</text>
<li style="list-style: none; color:#7770ff;">You can check whether a string is empty with the <code>blank</code> object.</li>

#### **number**
<li>Numeric values, including floats and integers.</li>

#### **boolean**
<li>A binary value, either <code>true</code> or <code>false</code></li>

#### **nil**
<li>An undefned value.</li>
<li>Tags or outputs that return <code>nil</code> don't prnt anything to the page. They are also treated as <code>false</code></li>
<span class="note-up">★·.·´¯\`·.·★ ɴᴏᴛᴇ★·.·´¯\`·.·★</span>
A string with the characters "nil" is not treated as the same as <code>nil</code>
<hr/>

#### **array**
<li>A list of variables of any type.</li>
<li>To access all of the items in an array, you can loop through each item in the array using a <code>for</code> or <code>tablerow</code> tag.</li>
<li>You can use square bracked [] notation to access a specific item in an array. Array indexing starts at zero.</li>
<li>You can't initialize arrays using only Liquid. You can, however, use the split filter to break a single string into an array of substrings.</li>

  {% raw %}
    you can't use this = {% assign fruits = ["orange","apple","peach"] %}
    {% assign fruits = "orange,apple,peach" | split ',' %}
    {% for fruit in fruits %}
      {{fruit}}
    {% endfor %}
  {% endraw %}
Output =
  {% assign fruits = "orange,apple,peach" | split: ',' %}
  {% for fruit in fruits %}
    {{fruit}}
  {% endfor %}

#### **empty**
<li>An <code>empty</code> object is returned if you try to access an object that is defined, but has no value. For example a page or product that's been deleted, or a setting with no value.</li>
<li>You can compare an object with <code>empty</code>to check whether an object exists before you access any of its attributes.</li>
  {% raw %}
    {% unless page.about-us == empty %}
      <h1>{{page.title}}</h1>
      <div>
        {{site.description}}
      </div>
    {% endunless %}
  {% endraw %}
Output =
  
  {% unless page.about-us == empty %}
      <h1>{{page.title}}</h1>
      <div>
        {{site.description}}-
      </div>
  {% endunless %}

### **Truthy and falsy**
<li>All data types must return either <code>true</code>or<code>false</code>. Those which return <code>true</code> by default are called truthy. Those that return <code>false</code> by default are called falsy.</li>
<table>
<tr>
  <th>Value</th>
  <th>Truthy</th>
  <th>Falsy</th>
</tr>
<tr>
  <td>true</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>false</td>
  <td></td>
  <td>✅</td>
</tr>
<tr>
  <td>nil</td>
  <td></td>
  <td>✅</td>
</tr>
<tr>
  <td>empty string</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>0</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>integer</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>float</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>aray</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>empty array</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>page</td>
  <td>✅</td>
  <td></td>
</tr>
<tr>
  <td>empty object</td>
  <td>✅</td>
  <td></td>
</tr>
</table>

#### **Example**
<li>Because <code>nil</code> and <code>false</code> are the only falsy values, you need to be careful how you check values in Liquid. A value might not be in the format you expect, but still be truthy.</li>
<li>For example, empty strings are truthy, so you need to check whether they're empty with <code>blank</code>.<code>EmptyDrop</code> objects are also truthy, so you need to check whether the object you're referencing is <code>empty</code></li>
  {% raw %}
    {% if settings.featured_potions_title != blank -%}
      {{ settings.featured_potions_title }}
    {%- else -%}
      No value for this setting has been selected.
    {%- endif %}
    {% unless pages.recipes == empty -%}
      {{ pages.recipes.content }}
    {%- else -%}
      No page with this handle exists.
    {%- endunless %}
  {% endraw %}
Output =

    No value for this setting has been selected.
    No page with this handle exists.

### **Truthy and falsy**
<li>Even if doesn't output text, any line of Liquid outputs a line in your rendered content. By including hyphens in your Liquid tag, you can strip any whitespace that your Liquid generates when rendered.</li>
<li>If you want to remove whitespace on only one side of the Liquid tag, then you can include the hyphen on either the opening or closing tag.</li>

    {% assign collection_size = 50 %}
    {% assign collection_title = 'Sale potions' %}
    {% assign collection_all_types = "Health,Health & Beauty,Invisibility,Water" | split: ',' %}
    {%- if collection_size > 0 -%}
      The '{{ collection_title }}' collection contains the following types of products:
    {%- for type in collection_all_types -%}
      {% unless type == blank %}
        - {{ type }}
      {%- endunless -%}
    {%- endfor %}
    {%- endif -%}

<a class="btn" href="#tags">Navigate to Basics</a>

## Tags
<li style="font-size:20px;">Liquid tags are used to define logic that tells templates what to do.</li>

### Usage
Tags are wrapped with curly brace percentage delimiters <code>{% raw %}{% %}{% endraw %}</code>. The text within the delimiters doesn't produce visible output when rendered.

In the example below, the <code>if</code> tag defines the condition to be met. If <code>product.available</code> returns <code>true</code>, then the price is displayed. Otherwise, the "sold-out" message is shown.

  {% raw %}
    {% if product.available %}
      Price: $99.99
    {% else %}
      Sorry, this product is sold out.
    {% endif %}
  {% endraw %}
Output =
    {% if product.available %}
      Price: $99.99
    {% else %}
      Sorry, this product is sold out.
    {% endif %} 
<span class="Vsw2a _22j2f" aria-label="Info Icon" role="img"><svg width="14" height="14" viewBox="0 0 14 14" fill="none" xmlns="http://www.w3.org/2000/svg" class="_2ak-2" focusable="false" aria-hidden="true"><path fill-rule="evenodd" clip-rule="evenodd" d="M0 12C0 13.1046 0.895431 14 2 14H12C13.1046 14 14 13.1046 14 12V2C14 0.895431 13.1046 0 12 0H2C0.89543 0 0 0.895431 0 2V12ZM6 4C6 3.44772 6.44772 3 7 3C7.55228 3 8 3.44772 8 4C8 4.55228 7.55228 5 7 5C6.44772 5 6 4.55228 6 4ZM7.5 6C7.77614 6 8 6.22386 8 6.5V9.5C8 9.77614 8.22386 10 8.5 10C8.77614 10 9 10.2239 9 10.5C9 10.7761 8.77614 11 8.5 11H8H6H5.5C5.22386 11 5 10.7761 5 10.5C5 10.2239 5.22386 10 5.5 10C5.77614 10 6 9.77614 6 9.5V7.5C6 7.22386 5.77614 7 5.5 7C5.22386 7 5 6.77614 5 6.5C5 6.22386 5.22386 6 5.5 6H7.5Z" fill="#6055FF"></path></svg></span><text style="color:#7770ff;font-weight:600;"> Tip</text>
<li style="list-style: none; color:#7770ff;">You can nest multiple tags inside one set of delimiters using the <u>liquid tag.</u></li>

### Tags with parameters
Certain tags accept parameters. Some tags have required parameters, and others are optional, For example, the <code>for</code> tag can accept parameters like <code>limit</code> to exit a loop at a specific index.
  {% raw %}
    {% assign numbers = '1,2,3,4,5' | split: ',' %}
    {% for item in numbers limit:2 -%}
      {{ item }}
    {%- endfor %}
  {% endraw %}
Output =
  {% assign numbers = '1,2,3,4,5' | split: ',' %}
  {% for item in numbers limit:2 %}
    {{ item }}
  {%- endfor %}

<span id="#conditional-tags">
### Conditional tags

