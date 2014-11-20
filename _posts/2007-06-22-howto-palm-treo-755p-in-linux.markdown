---
layout: post
status: publish
published: true
title: 'HOWTO: Palm Treo 755p in Linux'
author:
  display_name: Robert
  login: panthar
  email: panthar@gmail.com
  url: http://panthar.org/
author_login: panthar
author_email: panthar@gmail.com
author_url: http://panthar.org/
excerpt: |+
  I recently purchased a Palm Treo 755p.  One of the first things I did was to plug it into my Linux machine to try the syncing capabilities, since Linux distributions (I am currently using Ubuntu 7.04) tend to support Palm devices pretty well.  But, when I plugged it in, I discovered that it was not recognized by the kernel.  So, I figured out what was needed to make it function:

wordpress_id: 126
wordpress_url: http://panthar.org/2007/06/22/howto-palm-treo-755p-in-linux/
date: '2007-06-22 13:46:08 -0500'
date_gmt: '2007-06-22 17:46:08 -0500'
categories:
- HOWTO
- Linux
tags: []
comments: []
---
<p>I recently purchased a Palm Treo 755p.  One of the first things I did was to plug it into my Linux machine to try the syncing capabilities, since Linux distributions (I am currently using Ubuntu 7.04) tend to support Palm devices pretty well.  But, when I plugged it in, I discovered that it was not recognized by the kernel.  So, I figured out what was needed to make it function:</p>
<p><a id="more"></a><a id="more-126"></a></p>
<p>After poking through the kernel logs and watching udev events, I was able to make this device work perfectly:</p>
<p>I created the file:</p>
<pre>&#47;etc&#47;udev&#47;rules.d&#47;10-custom.rules<&#47;pre><br />
Inside this file, I inserted the following:</p>
<pre>SUBSYSTEM=="usb", ATTR{idVendor}=="0830", ATTR{idProduct}=="0061", \\<br />
    RUN+="&#47;sbin&#47;modprobe visor"<&#47;pre><br />
Then, I restarted udev (<code>&#47;etc&#47;init.d&#47;udev restart<&#47;code>) and the device works properly.  The correct module is loaded, &#47;dev&#47;ttyUSB0 and &#47;dev&#47;ttyUSB1 are created, and &#47;dev&#47;pilot is created, linking to the correct USB device.</p>
<p>If you have a different PalmOS-based device that is not loading properly, this can also work for you.  Just do:</p>
<pre>lsusb<&#47;pre><br />
and look for a line like:</p>
<pre>Bus 002 Device 020: ID 0830:0061 Palm, Inc.<&#47;pre><br />
Inside the 10-custom.rules file, use the values before and after the colon as the <code>ATTR{idVendor}<&#47;code> and <code>ATTR{idProduct}<&#47;code></p>
