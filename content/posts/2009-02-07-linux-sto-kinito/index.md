---
title: Linux.. running on.. κινητό!
date: 2009-02-07T20:03:49+00:00
url: /linux-sto-kinito/
categories:
  - Brainstorm
  - How-to και άλλα
tags:
  - j2me
  - java
  - linux
  - M600i
  - mobile

---
Όχι, δεν είναι μπαρούφες. Κάτι πολύ απλό που αξίζει να το δοκιμάσει κανείς! Να συμπληρώσω ότι **θεωρητικά** τρέχει ΟΛΑ τα x86 λειτουργικά συστήματα. Απλά τα Linux είναι αρκετά ελαφριά καταφέρνει να τα bootάρει, βγαίνουν και distro σε μέγεθος floppy.. τέλεια! 😛

Όλα τα κάνει το.. <a href="http://www-jpc.physics.ox.ac.uk" class="broken_link" rel="nofollow">JPC</a>. To JPC είναι emulator x86 γραμμένος σε Java! Υπάρχει έκδοση για υπολογιστή, applet και φυσικά.. για κινητό, σε alpha στάδιο ακόμη. Μπορείς να το δείς εν δράση, να τρέχει FreeDOS <a href="http://www-jpc.physics.ox.ac.uk/Demo.html" class="broken_link" rel="nofollow">εδώ</a> και Linux <a href="http://www-jpc.physics.ox.ac.uk/DemoLinux.html" class="broken_link" rel="nofollow">εδώ</a>.  
Όχι, δεν είναι μπαρούφες. Κάτι πολύ απλό που αξίζει να το δοκιμάσει κανείς! Να συμπληρώσω ότι θεωρητικά τρέχει ΟΛΑ τα x86 λειτουργικά συστήματα. Απλά τα Linux είναι αρκετά ελαφριά καταφέρνει να τα bootάρει, βγαίνουν και distro σε μέγεθος floppy.. τέλεια! 😛

Όλα τα κάνει το.. <a href="http://www-jpc.physics.ox.ac.uk" class="broken_link" rel="nofollow">JPC</a>. To JPC είναι emulator x86 γραμμένος σε Java! Υπάρχει έκδοση για υπολογιστή, applet και φυσικά.. για κινητό, σε Alpha στάδιο ακόμη.  
Μπορείς να το δείς εν δράση, να τρέχει FreeDOS <a href="http://www-jpc.physics.ox.ac.uk/Demo.html" class="broken_link" rel="nofollow">εδώ</a> και Linux <a href="http://www-jpc.physics.ox.ac.uk/DemoLinux.html" class="broken_link" rel="nofollow">εδώ</a>.

To the point τώρα! Πηγαίνοντας <a href="http://www-jpc.physics.ox.ac.uk/getjpc.html" class="broken_link" rel="nofollow">εδώ</a> βλέπεις τις εκδόσεις που υπάρχουν. Κάνε focus κάτω-κάτω, εκεί που λέει &#8220;**Download the Mobile Demo Application**&#8220;. Έχει ένα link για το [.jad](http://en.wikipedia.org/wiki/JAD_(file_format)). Βάζοντας αυτό το αρχείο στον browser του κινητού θα κατεβάσει αυτόματα το πρόγραμμα. Δεν χρειάζεται να το κάνεις βέβαια. Κάνε κλικ <a href="http://www-jpc.physics.ox.ac.uk/mobile/JPC.jar" class="broken_link" rel="nofollow">εδώ</a> και κατέβασέ το στο PC, όπου μπορείς να το περάσεις στο κινητό μετά (μέσω Bluetooth ή μέσω καλωδίου, IrDA, WiFi, brain waves κτλ).

Πάρα μα πάρα πολύ πιθανό είναι να πετάξει error ότι είναι out of memory! Το K750i που το δοκίμασα δηλαδή, πέταξε. Λογικό ακούγεται γιατί έχει μόλις 2mb RAM.. Στο M600i τώρα, με [δυστυχώς](http://www.google.com/search?q=memory+leak+m600), 64mb RAM τρέχει. Μερικά λειτουργικά μόνο πετάξανε αυτό το error και μέσα σε αυτά το [DSL](http://www.damnsmalllinux.org/) όταν πάλευε να ξεκινήσει, αφού περίμενα 5 λεπτά να βγάλει όλη την εικόνα που έχει στο boot.

Για να αντικαταστήσεις το image του floppy που έχει μέσα το κάνεις με το WinRAR. Ανοίγεις το .jar, σβήνεις το floppy.img και βάζεις το δικό σου. Προσοχή, να έχει όνομα ίδιο με το προηγούμενο, δηλαδή _floppy.img_ και να είναι image από floppy έκδοση.

To the point τώρα! Πηγαίνοντας <a href="http://www-jpc.physics.ox.ac.uk/getjpc.html" class="broken_link" rel="nofollow">εδώ</a> βλέπεις τις εκδόσεις που υπάρχουν. Κοίτα κάτω-κάτω, εκεί που λέει &#8220;**Download the Mobile Demo Application**&#8220;. Έχει ένα link για το [.jad](http://en.wikipedia.org/wiki/JAD_(file_format)). Βάζοντας αυτό το URL στον browser του κινητού θα κατεβάσει αυτόματα το πρόγραμμα. Δεν χρειάζεται να το κάνεις έτσι βέβαια, κάνε οικονομία στο bandwidth μιας και πληρώνεις ανά byte. Κάνε κλικ <a href="http://www-jpc.physics.ox.ac.uk/mobile/JPC.jar" class="broken_link" rel="nofollow">εδώ</a> και κατέβασέ το στο PC, όπου μπορείς να το περάσεις στο κινητό μετά (μέσω Bluetooth ή μέσω καλωδίου, IrDA, WiFi, brainwaves κτλ).

Πάρα, μα πάρα, πολύ πιθανό είναι να πετάξει error ότι είναι out of memory! Το [K750i](http://www.gsmarena.com/sony_ericsson_k750-1090.php) που το δοκίμασα δηλαδή, πέταξε. Λογικό ακούγεται γιατί έχει μόλις 2mb RAM (dedicated στο JVM εννοώ).. Στο [M600i](http://www.gsmarena.com/sony_ericsson_m600-1425.php) τώρα 64mb RAM, τρέχει. Μερικά λειτουργικά μόνο πετάξανε αυτό το error και μέσα σε αυτά το [DSL](http://www.damnsmalllinux.org/) όταν πάλευε να ξεκινήσει, αφού περίμενα 5 λεπτά να βγάλει όλη την εικόνα που έχει στο boot. Κάπου στο site τους λέει ότι δεν γίνεται να bootάρεις σε GUI για κάποιο λόγο, αλλά εδώ θα κωλώσουμε ωρέ? 😛

Για να αντικαταστήσεις το image του floppy που έχει μέσα το κάνεις με το WinRAR. Ανοίγεις το .jar, σβήνεις το floppy.img και βάζεις το δικό σου. Προσοχή, να έχει όνομα ίδιο με το προηγούμενο, δηλαδή _floppy.img_ και να είναι image από floppy έκδοση. Αυτό μόνο! 😉

Καλό.. κάψιμο!

_Αυτό το άρθρο ήταν draft απ&#8217; το καλοκαίρι.._
