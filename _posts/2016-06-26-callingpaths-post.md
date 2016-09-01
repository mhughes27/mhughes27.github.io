---
layout: post
title: "Calling Paths"
date: 2016-06-26
excerpt: "How to call paths"
tags: [paths, php]
feature: http://i.imgur.com/Ds6S7lJ.png
comments: false
---

Calling Paths

Links

Given the following file structure for:

personal_website/

index.php
goals.php
navigation.php
pets/
fido.php
cat.php
articles/
about_facebook.php
how_the_web_works.php
Here is how the links behave given the following scenarios linked from index.php:

<a href="goals.php">Goals</a> The page displays properly. This is the correct way to link pages in the same directory. goals.php and index.php are equals in the file hierarchy structure.

<a href="/goals.php">Goals</a> This page does not display properly. You get an error message saying that the requested URL cannot be found on the server. This link would work if the goals.php file was downstream from the index.php file.

<a href="../goals.php">Goals</a> This page does not display properly either. You get the same error message saying that the requested URL cannot be found on the server. This link would work if the goals.php file was upstream from the index.php file.

<a href="http://localhost:8888/personal_website/goals.php">Goals</a> This page does display properly, but it would not be available to anyone not using your computer. This provides the page using a local server. You can use it to see if your website is looking and functioning the way it should, but others will not be able to see it even after you upload your files to the web using a FTP like FileZilla.

Here is how the links behave given the following scenarios linked from pets/cat.php:

<a href="goals.php">Goals</a> This page does not display properly. Goals.php is located upstream from cats.php which is located in a folder named "pets".

<a href="/goals.php">Goals</a> This page does not display properly. You get an error message saying that the requested URL cannot be found on the server. This link would work if the goals.php file was downstream from the pets/cat.php file.

<a href="../goals.php">Goals</a> This page does display properly. This is the ways to correctly link a page that is upstream from the one you are currently on.

<a href="http://localhost:8888/personal_website/goals.php">Goals</a> This page does display properly, but it would not be available to anyone not using your computer. This provides the page using a local server. You can use it to see if your website is looking and functioning the way it should, but others will not be able to see it even after you upload your files to the web using a FTP like FileZilla.

Includes

Here is how the include() would behave given the following scenarios linked from index.php:

<?php include("navigation.php"); ?> The navigation displays correctly. index.php and navigation.php are in the same directory. They are on the same level.

<?php include("/navigation.php"); ?> The navigation does not display correctly. This would work if navigation.php was downstream from index.php. That how ever is not the case.

<?php include("../navigation.php"); ?> The navigation does not display correctly. This would work if navigation.php was upstream from index.php

Here is how the include() would behave given the following scenarios linked from articles/how_the_web_works.php:

<?php include("navigation.php"); ?> The navigation does not display correctly. navigation.php and articles/how_the_web_works.php are not on the same level. how_the_web_works.php is located in a folder downstream from navigation.php

<?php include("/navigation.php"); ?> The navigation does not display correctly. navigation.php is not downstream from articles/how_the_web_works.php.

<?php include("../navigation.php"); ?> The navigation displays properly. This is the correct way to include something that is upstream from where your current page is located.