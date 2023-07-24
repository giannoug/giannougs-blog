---
title: Setάροντας έναν VPS. Επεισόδιο 2ον.
date: 2009-01-06T19:16:28+00:00
url: /setarontas-enan-vps-part-ii/
categories:
  - How-to και άλλα
tags:
  - debian
  - guide
  - server
  - Setάροντας έναν VPS
  - vps

---
Εύχομαι να τα είπα καλά στο προηγούμενο post και να βοήθησα μερικούς ή να τους έδωσα κάποιες ιδέες. Σε αυτό το part θα γράψω κάτι πιο πιασάρικο και χρήσιμο 😉 😛

**Πως κάνουμε τον VPS μας web server!** Επιτέλους στο ζουμί 😛 Χωρίς πολλά πολλά, ξεκινάμε.  


Δεν μας χρειάζεται τίποτα από το προηγούμενο μέρος. Δεν πιστεύω να χρειαστεί γενικά στα επόμενα μέρη τίποτα απ&#8217; τα προηγούμενα.

### 1. Εγκατάσταση lighttpd

Όχι εντάξει, είπαμε. Δεν θα κάνουμε compile από sources -ακόμα-. Αντιθέτως θα χρησιμοποιήσουμε τα compiled απ&#8217; τα repositories του Debian, all time classic _apt_ δηλαδή 😉

{{< highlight bash >}}
  root@Slave-PC:~$ apt-get install lighttpd
{{< / highlight >}}

Για να εγκαταστήσουμε τον web server μας.

Τώρα, γιατί lighttpd.. Λένε ότι είναι πιο γρήγορος. Εγώ θα πω είναι πιο εύκολος. Έχει καλύτερο config. Είμαι ανώμαλος μάλλον. Προτείνω lighttpd λοιπόν 😛

Για να βεβαιωθούμε ότι τρέχει σωστά, βάζουμε την IP του server στον browser. Θα δεις το placeholder page του lighttpd 🙂

Όπως όλα τα config των προγραμμάτων, έτσι και του lighttpd, πήγε στο /etc! Μπορούμε να το tweakάρουμε λίγο για να ικανοποιήσει πλήρως τις ανάγκες μας. Δεν θα το κάνουμε ακόμα όμως. Οι σελίδες που σερβίρει μπαίνουν στο _/var/www_. Οδηγίες για virtual hosts θα μπουν στα τελευταία part της σειράς unless otherwise stated 😛 🙂

Συνεχίζουμε με PHP!

### 2. Εγκατάσταση PHP

Όπως και με τον lighttpd, έτσι και εδώ θα χρησιμοποιήσουμε τα repo για να περάσουμε την PHP! Get used to it 😛

{{< highlight bash >}}
  root@Slave-PC:~$ apt-get install php5-cgi
{{< / highlight >}}

Για να κάνουμε τον lighttpd να _τρέχει_ τα php, πρέπει να περάσουμε ένα module. Πριν το περάσουμε όμως, θέλει μια διόρθωση.

{{< highlight bash >}}
  root@Slave-PC:~$ cd /etc/lighttpd/conf-available
{{< / highlight >}}

Για να πάμε στο φάκελο των module και..

{{< highlight bash >}}
  root@Slave-PC:~$ nano 10-fastcgi.conf
{{< / highlight >}}

..για να το ανοίξουμε με το nano.  
_(Το έσπασα σε 2 εντολές γιατί αν το έκανα 1 πήγαινε στην από κάτω και φαινότανε άσχημα)_  
Μόλις ανοίξει ο nano, πηγαίνουμε στην γραμμή που λέει _&#8220;bin-path&#8221; => &#8220;/usr/bin/php4-cgi&#8221;_ και την αλλάζουμε σε _&#8220;bin-path&#8221; => &#8220;/usr/bin/php**5**-cgi&#8221;_.  
Δεν θέλουμε PHP4, σωστά? 😛

Θα χρειαστούμε ακόμη ένα πακέτο για να δουλέψει η PHP με την MySQL. Τρέχουμε..

{{< highlight bash >}}
  root@Slave-PC:~$ apt-get install php5-mysql
{{< / highlight >}}

Επιπλέον, αν χρειαστείς τίποτα άλλο, για παράδειγμα GD στην PHP πρέπει να εγκαταστήσεις το αντίστοιχο module, στην συγκεκριμένη περίπτωση το _php5-gd_.  
Ένας πίνακας με τα διαθέσιμα modules για την PHP:

> php-imlib &#8211; PHP Imlib2 Extension  
> php-pear &#8211; PEAR &#8211; PHP Extension and Application Repository  
> php5-auth-pam &#8211; A PHP5 extension for PAM authentication  
> php5-curl &#8211; CURL module for php5  
> php5-ffmpeg &#8211; ffmpeg support for php5  
> php5-gd &#8211; GD module for php5  
> php5-geoip &#8211; GeoIP module for php5  
> php5-gmp &#8211; GMP module for php5  
> php5-gpib &#8211; libgpib PHP5 bindings  
> php5-idn &#8211; PHP API for the IDNA library  
> php5-imagick &#8211; ImageMagick module for php5  
> php5-imap &#8211; IMAP module for php5  
> php5-interbase &#8211; interbase/firebird module for php5  
> php5-ldap &#8211; LDAP module for php5  
> php5-librdf &#8211; PHP5 language bindings for the Redland RDF library  
> php5-mapscript &#8211; php5-cgi module for MapServer  
> php5-mcrypt &#8211; MCrypt module for php5  
> php5-memcache &#8211; memcache extension module for PHP5  
> php5-mhash &#8211; MHASH module for php5  
> php5-ming &#8211; Ming module for php5  
> php5-mysql &#8211; MySQL module for php5  
> php5-odbc &#8211; ODBC module for php5  
> php5-pgsql &#8211; PostgreSQL module for php5  
> php5-ps &#8211; ps module for PHP 5  
> php5-pspell &#8211; pspell module for php5  
> php5-radius &#8211; PECL radius module for PHP 5  
> php5-recode &#8211; recode module for php5  
> php5-sasl &#8211; Cyrus SASL extension for PHP 5  
> php5-snmp &#8211; SNMP module for php5  
> php5-sqlite &#8211; SQLite module for php5  
> php5-sqlrelay &#8211; SQL Relay PHP API  
> php5-suhosin &#8211; advanced protection module for php5  
> php5-svn &#8211; PHP Bindings for the Subversion Revision control system  
> php5-sybase &#8211; Sybase / MS SQL Server module for php5  
> php5-syck &#8211; YAML parser kit &#8212; PHP5 bindings  
> php5-symfony1.0 &#8211; Open-Source PHP Web Framework  
> php5-tidy &#8211; tidy module for php5  
> php5-uuid &#8211; OSSP uuid module for php5  
> php5-xapian &#8211; Xapian search engine interface for PHP5  
> php5-xcache &#8211; Fast, stable PHP opcode cacher  
> php5-xdebug &#8211; Xdebug Module for PHP 5  
> php5-xmlrpc &#8211; XML-RPC module for php5  
> php5-xsl &#8211; XSL module for php5 

_Απ&#8217; το apt-cache τα πήρα 😛_

Τέλος τρέχουμε..

{{< highlight bash >}}
  root@Slave-PC:~$ lighttpd-enable-mod fastcgi
{{< / highlight >}}

..για να ενεργοποιηθεί το module και..

{{< highlight bash >}}
  root@Slave-PC:~$ /etc/init.d/lighttpd restart
{{< / highlight >}}

..για να κάνουμε restart τον lighttpd.

Για να τον testάρεις τώρα. Τρέξε..

{{< highlight bash >}}
  root@Slave-PC:~$ echo &#8220;< ? phpinfo(); ?>&#8221; > /var/www/phpinfo.php
{{< / highlight >}}

Αυτό θα φτιάξει ένα αρχείο PHP με περιεχόμενο το _< ? phpinfo(); ?>_. Αν, τώρα, βάλεις _http://ip.tou.server/phpinfo.php_ στον browser σου θα δεις ένα.. κατεβατό. Αυτό σημαίνει ότι όλα πήγαν καλά και ότι η PHP τρέχει 🙂 Μπορείς να συνεχίσεις με την..

### 3. Εγκατάσταση MySQL

{{< highlight bash >}}
  root@Slave-PC:~$ apt-get install mysql-server mysql-client
{{< / highlight >}}

Με αυτή την εντολή, εκτός απ&#8217; την MySQL, εγκαθιστούμε και ένα client για να μπορείς να την διαχειρίζεσαι μέσω cli. Αν δεν γουστάρς, απλά σβήσε το mysql-client απ&#8217; την εντολή 😉

Αφήνουμε default ότι ρωτήσει αν και δεν νομίζω ότι ρωτάει τίποτα **εκτός** από τον κωδικό για τον root χρήστη. Βάλε κάτι πρωτότυπο και πρόσεχε **ΜΗΝ** το ξεχάσεις.

Σε μερικούς VPS, λόγο του ότι δεν έχουνε αρκετή RAM (128mb) δεν ξεκινάει και βγάζει προβλήματα. Εάν ψάξεις στα διάφορα forum των παρόχων VPS σίγουρα θα βρεις κάποιες ρυθμίσεις. Για αρχή-testing, μπορείς να χρησιμοποιήσεις αυτές.  
Πρέπει να μπουν στο _/etc/mysql/my.cnf_. Πως να το επεξεργαστείς το έχεις μάθει, πιστεύω, πλέον 😛

> [mysqld]  
> port = 3306  
> socket = /var/run/mysqld/mysqld.sock
> 
> \# No locking at all!  
> skip-locking
> 
> \# Set internal buffers, caches and stacks very low  
> key_buffer = 16K  
> max\_allowed\_packet = 32M  
> table_cache = 1  
> sort\_buffer\_size = 16K  
> read\_buffer\_size = 16K  
> read\_rnd\_buffer_size = 1K  
> net\_buffer\_length = 1K  
> thread_stack = 16K
> 
> \# Don&#8217;t listen on a TCP/IP port at all.  
> \# Will still work provided all access is done via localhost  
> skip-networking  
> server-id = 1
> 
> \# Skip Berkley and Inno DB types  
> skip-bdb  
> skip-innodb
> 
> \# Set the query cache low  
> query\_cache\_limit = 1048576  
> query\_cache\_size = 1048576  
> query\_cache\_type = 1
> 
> \# Set various memory limits very low, disable memory-hogging extras  
> [mysqldump]  
> quick  
> max\_allowed\_packet = 16K
> 
> [mysql]  
> no-auto-rehash
> 
> [isamchk]  
> key_buffer = 16K  
> sort\_buffer\_size = 16K
> 
> [myisamchk]  
> key_buffer = 16K  
> sort\_buffer\_size = 16K 

Μην ξεχάσεις ότι μετά από το edit πρέπει να κάνεις restart τον server. Το restart γίνεται έτσι:

{{< highlight bash >}}
  root@Slave-PC:~$ /etc/init.d/< προγράμμα> restart
{{< / highlight >}}

Όπου < όνομα προγράμματος>, το όνομα του προγράμματος που θέλεις να επανεκκινήσεις!

Για να δεις αν η MySQL τρέχει, μπορείς να ξαναπάς στην σελίδα που δοκίμασες την PHP πριν και να δεις αν έχει φορτώσει το module για την ΜySQL 😉

Ωραία, φτιάξαμε την βάση δεδομένων.. πρέπει όμως κάπως να την διαχειριζόμαστε! Ένα \*αρκετά\* βολικό, και σε σχέση με το mysql-client απλό, εργαλείο είναι το phpMyAdmin. Το ίδιο απλή είναι και η εγκατάστασή του! 😛

{{< highlight bash >}}
  root@Slave-PC:~$ apt-get install phpmyadmin
{{< / highlight >}}

Έτοιμο. Αν τώρα πας στο _http://ip.tou.server/phpmyadmin/_ θα το δεις να δεσπόζει! Username βάζεις root και Password αυτό που έβαλες κατά την εγκατάσταση της MySQL.

Τέλος και το δεύτερο part! 😀  
Αυτά από &#8216;μένα. Από την στιγμή που δημοσιεύονται τα άρθρα, γίνονται κάποιες μικρο-αλλαγές.  
Δεν μπορώ να φανταστώ καμιά φορά τι μαλακίες γράφω xD  
Ότι λάθος έχω κάνει, comment με 😉  
Τα λέμε.