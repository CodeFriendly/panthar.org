---
layout: post
status: publish
published: true
title: 'HOWTO: PHP with MSSQL on Ubuntu 6.06'
author:
  display_name: Robert
  login: panthar
  email: panthar@gmail.com
  url: http://panthar.org/
author_login: panthar
author_email: panthar@gmail.com
author_url: http://panthar.org/
excerpt: |+
  I recently set up an Ubuntu server that needed to access a MSSQL database. The php5-sybase package sort of worked (the queries appeared to work, but data was missing). So, I set out to build some .deb packages with MSSQL support built in.

wordpress_id: 113
wordpress_url: http://panthar.org/2006/06/15/php-with-mssql-on-ubuntu-606/
date: '2006-06-15 18:38:32 -0500'
date_gmt: '2006-06-15 22:38:32 -0500'
categories:
- Coding
- HOWTO
- Internet
- Linux
tags: []
comments:
- id: 3
  author: Matt
  author_email: matthewjamesnewton@gmail.com
  author_url: ''
  date: '2007-01-03 10:46:37 -0600'
  date_gmt: '2007-01-03 14:46:37 -0600'
  content: |-
    Ranouf, I have the same problem....

    root@linux:~&#47;php5-5.1.6# dpkg-buildpackage
    dpkg-buildpackage: source package is php5
    dpkg-buildpackage: source version is 5.1.6-1ubuntu2.1
    dpkg-buildpackage: source changed by Martin Pitt
    dpkg-buildpackage: host architecture i386
    dpkg-buildpackage: source version without epoch 5.1.6-1ubuntu2.1
    dpkg-checkbuilddeps: error: per-package paragraph 23 in control info file is missing Package line
    dpkg-buildpackage: Build dependencies&#47;conflicts unsatisfied; aborting.
    dpkg-buildpackage: (Use -d flag to override.)
- id: 4
  author: Matt
  author_email: matthewjamesnewton@gmail.com
  author_url: ''
  date: '2007-01-03 11:54:12 -0600'
  date_gmt: '2007-01-03 15:54:12 -0600'
  content: |-
    sorry... Ignore my last post... It was due to extra spaces after I pasted into the control file... I do have another problem through. After I try to do a dpkg-build package I get the following. This will be the second tutorial that this has happened to me on. I'm not sure why either.

    root@linux:~&#47;php5-5.1.6# dpkg-buildpackage
    dpkg-buildpackage: source package is php5
    dpkg-buildpackage: source version is 5.1.6-1ubuntu2.1
    dpkg-buildpackage: source changed by Martin Pitt
    dpkg-buildpackage: host architecture i386
    dpkg-buildpackage: source version without epoch 5.1.6-1ubuntu2.1
     debian&#47;rules clean
    : No such file or directory
    '.  Stop. No rule to make target `

    I think i'm going to try and use an older verison of PHP.
- id: 5
  author: Stephen
  author_email: spamed.alot@gmail.com
  author_url: ''
  date: '2007-01-23 20:50:36 -0600'
  date_gmt: '2007-01-24 00:50:36 -0600'
  content: |-
    great stuff, just finished my 4th build of this on a different machine over the past 6 weeks!

    Matt: If you move up to the parent folder the php5-mssql extension should have been built anyway, just install it with dpkg -i, worked perfectly for me!
- id: 6
  author: Sam Alex
  author_email: samalex@gmail.com
  author_url: ''
  date: '2007-05-07 11:59:49 -0500'
  date_gmt: '2007-05-07 15:59:49 -0500'
  content: |-
    Hi Everyone.  I went through this tutorial, and all went as expected.  However after installation, I ran the following:

    -- Installed the newly compiled packages
    dpkg -i php5-mysql_5.1.6-1ubuntu2.4_i386.deb
    dpkg -i php5-mysqli_5.1.6-1ubuntu2.4_i386.deb
    -- Restarted Apache services
    &#47;etc&#47;init.d&#47;apache2 restart

    This is all on Ubuntu 6.10 Server setup with LAMP during installation.  Next I tried to run the follow script to test this, of course I plugged in my server's IP Address and login info, plus a valid database and table.:



    ", "sa", "");
    mssql_select_db ("", $con);
    $sql= "SELECT * FROM ";
    $rs= mssql_query ($sql, $con);
    echo "The field number one is: ";
    echo mssql_result ($rs, 0, 0);
    mssql_close ($con);
    ?>



    And now here's what I get:


    Fatal error: Call to undefined function mssql_connect() in &#47;home&#47;webuser&#47;public_html&#47;test.php on line 4

    Any suggestions?  Is there anyway to to verify the new packages are installed correctly?

    Thanks for any suggestions.
    Sam Alexander
    samalex@gmail.com
- id: 7
  author: Robert
  author_email: panthar@gmail.com
  author_url: http://panthar.org/
  date: '2007-05-07 12:51:43 -0500'
  date_gmt: '2007-05-07 16:51:43 -0500'
  content: |-
    @Sam Alex:

    I noticed that you installed "dpkg -i php5-mysql_5.1.6-1ubuntu2.4_i386.deb".
    You need to install the .deb with "mssql" in the name, not "mysql", if you need to get mssql functionality.
    It gets built into its own package, not bundled in with mysql.
    Hope this solves your problem!

        -Robert
- id: 8
  author: Adventures in Nerdville &raquo; Blog Archive &raquo; php5-gmp in Gutsy
  author_email: ''
  author_url: http://www.vortex-tech.com/blog/?p=11
  date: '2008-03-17 16:50:10 -0500'
  date_gmt: '2008-03-17 20:50:10 -0500'
  content: '[...] http:&#47;&#47;ubuntuforums.org&#47;showpost.php?p=3198941&amp;postcount=9
    [...]'
- id: 9
  author: Web Technologie &raquo; Ubuntu et sa mise &agrave; jour
  author_email: ''
  author_url: http://web.t.free.fr/?p=12
  date: '2008-08-05 04:31:53 -0500'
  date_gmt: '2008-08-05 08:31:53 -0500'
  content: '[...] Pour infos le billet que j&#8217;ai trouv&eacute; sur internet me
    permettant de compiler avec l&#8217;option MSSQL: ici [...]'
- id: 10
  author: Robert
  author_email: panthar@gmail.com
  author_url: http://panthar.org/
  date: '2007-03-30 07:36:53 -0500'
  date_gmt: '2007-03-30 12:36:53 -0500'
  content: Thank you Matt and Robin for catching the extra blank line in the control
    file.  When I first wrote this, it worked as in this article, but when updating
    my PHP installation on 6.10 more recently, I came across the same issue.  I just
    forgot to update it in this article - thank you for reminding me, and I have fixed
    the code above.
- id: 11
  author: Robert
  author_email: panthar@gmail.com
  author_url: http://panthar.org/
  date: '2006-07-10 12:44:36 -0500'
  date_gmt: '2006-07-10 17:44:36 -0500'
  content: 'You do not have to uninstall your older PHP packages - this will overwrite&#47;upgrade
    it (it won''t mess with your config files)<br><br>To keep this from being upgraded
    automatically, you should "pin" it.  There is a good reference for that over at:
    <a href="http:&#47;&#47;www.debian.org&#47;doc&#47;manuals&#47;apt-howto&#47;ch-apt-get.en.html#s-pin"
    rel="nofollow">http:&#47;&#47;www.debian.org&#47;doc&#47;manuals&#47;apt-howto&#47;ch-...<&#47;a>'
- id: 12
  author: Santy
  author_email: cloudglider@aol.com
  author_url: ''
  date: '2006-06-26 15:47:31 -0500'
  date_gmt: '2006-06-26 20:47:31 -0500'
  content: 'Please ignore my last post... I know now why It didn''t work: I think
    I entered dpkg -i php5_*.deb and that did not install the mssql deb... i explicitly
    installed the mssql deb and it worked... thanks'
- id: 13
  author: Ian Tomkinson
  author_email: noemail@intensedebate.com
  author_url: ''
  date: '2009-02-18 15:37:16 -0600'
  date_gmt: '2009-02-18 15:37:16 -0600'
  content: Just wanted to confirm that this method works on the new Debian lenny release.
    However it seems to have a problem with imap, and the deb build failed with errors
    on php_imap.c. I don&#039;t need IMAP so I just disabled it in the rules by setting
    the two lines with imap to --without. If php with imap &amp; mssql is crucial
    to you, take care before upgrading to lenny.
- id: 14
  author: Tom
  author_email: noemail@intensedebate.com
  author_url: ''
  date: '2009-04-01 08:35:04 -0500'
  date_gmt: '2009-04-01 08:35:04 -0500'
  content: |-
    So i&#039;ve followed the guide and installed php5-mssql_5.2.6-2ubuntu4.1_i386.deb.

    What do I need to do now to test it?
- id: 15
  author: Steve
  author_email: sblaurock@gmail.com
  author_url: ''
  date: '2009-07-08 16:19:26 -0500'
  date_gmt: '2009-07-08 16:19:26 -0500'
  content: How long does it take for the process to complete? Mine has been going
    for a very long time, seems like it is looping as well... Any comments?
---
<p>I recently set up an Ubuntu server that needed to access a MSSQL database. The php5-sybase package sort of worked (the queries appeared to work, but data was missing). So, I set out to build some .deb packages with MSSQL support built in.</p>
<p><a id="more"></a><a id="more-113"></a></p>
<p>First make sure you have the Debian package development tools:</p>
<p><code>apt-get install build-essential debhelper<&#47;code></p>
<p>(More tools might be needed depending on what you already have installed, but you will tend to get warnings about what is missing)</p>
<p>Then, download the PHP sources:</p>
<p><code>apt-get source php5<&#47;code></p>
<p>(The current version in the Ubuntu repositories at this time is php5-5.1.2, so adjust for version numbers in the future.)</p>
<p>And you will need all the dependencies for building PHP:</p>
<p><code>apt-get build-dep php5<&#47;code></p>
<p>Change into the debian build directory for PHP:</p>
<p><code>cd php5-5.1.2&#47;debian<&#47;code></p>
<p>The first step is to edit the &acirc;&euro;&oelig;modulelist&acirc;&euro;? file. Insert a line above the one that says</p>
<p><code>mysql MySQL<&#47;code></p>
<p>with the contents:</p>
<p><code>mssql MSSQL<&#47;code></p>
<p>Next, edit the file "rules" and look for the section starting with "configure-apache2-stamp". You will see a line similar to:</p>
<p><code>--with-mysql=shared,&#47;usr<&#47;code></p>
<p>Open a line above this with the contents:</p>
<p><code>--with-mssql=shared,&#47;usr<&#47;code></p>
<p>Make sure not to forget the backslash on the end.Now, we must edit the "control" file in the same directory.  Add this to the end of the file:</p>
<pre style="font-size: 11px">Package: php5-mssql<br />
Architecture: any<br />
Depends: ${shlibs:Depends}, ${misc:Depends}, ${php:Depends}, php5-common (= ${Source-Version})<br />
Description: MSSQL module for php5<br />
 This package provides a module for MSSQL using FreeTDS.<br />
 .<br />
 PHP5 is an HTML-embedded scripting language. Much of its syntax is borrowed<br />
 from C, Java and Perl with a couple of unique PHP-specific features thrown<br />
 in. The goal of the language is to allow web developers to write<br />
 dynamically generated pages quickly.<&#47;pre><br />
Move up a directory.</p>
<p><code>cd ..<&#47;code></p>
<p>Now, run:</p>
<p><code>dpkg-buildpackage<&#47;code></p>
<p>And go get something to eat. This will do the whole configure&#47;compile for PHP and create debs in the parent directory. When this process is done, move up to the parent directory:</p>
<p><code>cd ..<&#47;code></p>
<p>And, you will see all of the PHP debs, including the new php5-mssql_[version].deb</p>
<p>Run a dpkg -i on the ones you need, and you should be all set to connect to MSSQL databases.</p>
<p><!-- technorati tags begin --></p>
<p style="font-size: 10px; text-align: right">technorati tags:<a href="http:&#47;&#47;technorati.com&#47;tag&#47;php" rel="tag">php<&#47;a>, <a href="http:&#47;&#47;technorati.com&#47;tag&#47;mssql" rel="tag">mssql<&#47;a>, <a href="http:&#47;&#47;technorati.com&#47;tag&#47;ubuntu" rel="tag">ubuntu<&#47;a><&#47;p><br />
<!-- technorati tags end --></p>
