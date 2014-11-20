---
layout: post
status: publish
published: true
title: Rounded Plurks
author:
  display_name: Robert
  login: panthar
  email: panthar@gmail.com
  url: http://panthar.org/
author_login: panthar
author_email: panthar@gmail.com
author_url: http://panthar.org/
wordpress_id: 191
wordpress_url: http://panthar.org/?p=191
date: '2008-08-14 14:08:38 -0500'
date_gmt: '2008-08-14 18:08:38 -0500'
categories:
- Plurk
tags: []
comments:
- id: 20
  author: nadine
  author_email: kitcat_chii@yahoo.com
  author_url: http://ninjaakoniyanski.wordpress.com
  date: '2008-12-03 12:01:29 -0600'
  date_gmt: '2008-12-03 12:01:29 -0600'
  content: thanksss for this :]
---
<p>I am working on getting the Plurk boxes rounded to look a little nicer.&nbsp; I have some early CSS written up that almost works, but I am having a hard time making the right hand border line up when a plurk is expanded. I think it has to do with that width being dynamically hard-coded. Yes, that sounds a bit odd, but it's basically on page load, the plurk code sets a static width on the expanded box.</p>
<p>So, I am looking into fun tricks like negative margins and&#47;or padding, but not having too much luck so far.&nbsp; For anyone that wants to use what I have so far, here is the CSS ( it also includes a piece to round your dashboard):</p>
<blockquote>
<pre>#plurk-dashboard&nbsp; {</p>
<p>color: #ffffff;<br />
margin: 0 5px;<br />
padding: 10px;<br />
border: 2px solid #ffffff;<br />
-moz-border-radius: 6px;<br />
-khtml-border-radius: 6px;<br />
-webkit-border-radius: 6px;<br />
border-radius: 6px;<br />
}</p>
<p>.plurk_cnt&nbsp; {<br />
border: 1px solid #000000;<br />
-moz-border-radius: 3px;<br />
-khtml-border-radius: 3px;<br />
-webkit-border-radius: 3px;<br />
border-radius: 3px;<br />
}</p>
<p>#form_holder<br />
{<br />
border-right: 1px solid #000000;<br />
border-left: 1px solid #000000;<br />
}<&#47;pre><br />
<&#47;blockquote></p>
