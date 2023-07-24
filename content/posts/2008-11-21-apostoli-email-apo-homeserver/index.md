---
title: Αποστολή email από home server ^_^
date: 2008-11-21T21:18:47+00:00
url: /apostoli-email-apo-homeserver/
categories:
  - How-to και άλλα
tags:
  - home server
  - linux
  - mail
  - postfix
  - smtp

---
Για τους γνώστες του αντικειμένου είναι εύκολο. Υπάρχει ένα μικρό σημείο, στα config, όμως που μπορεί να σου χαλάσει τα σχέδια 😛 Δεν εννοώ πως να στείλεις email από κάποια υπηρεσία, αλλά από το PC σου ή κάποιον server μέσω κάποιου [server](http://en.wikipedia.org/wiki/Mail_transfer_agent) (με την έννοια του MTA).  


Δυστυχώς από δυναμική (dynamic) IP δεν μπορείς να στέλνεις email έτσι απλά, για λόγους αποφυγής spamming και κουραφέξαλα. Βασικά μπορείς! Αλλά τρως πόρτα από τον server του email που θες να στείλεις.. (δοκίμασα τους 3 βασικούς παρόχους, GMail &#8211; Live Mail &#8211; Yahoo Mail, όλοι το ίδιο).

Τρανό παράδειγμα:

> This is the mail system at host Slave-PC.WAG54GS.
> 
> I&#8217;m sorry to have to inform you that your message could not  
> be delivered to one or more recipients. It&#8217;s attached below.
> 
> For further assistance, please send mail to postmaster.
> 
> If you do so, please include this problem report. You can  
> delete your own text from the attached returned message.
> 
> The mail system
> 
> : host gmail-smtp-in.l.google.com[72.14.221.114] said:  
> 550-5.7.1 [77.49.112.75] The IP you&#8217;re using to send mail is not authorized  
> 550-5.7.1 to send email directly to our servers. **_Please use the SMTP_**  
> 550-5.7.1 **_relay at your service provider instead_**. Learn more at 550  
> 5.7.1 http://mail.google.com/support/bin/answer.py?answer=10336  
> d4si6005819fga.8 (in reply to end of DATA command)
> 
> Reporting-MTA: dns; Slave-PC.WAG54GS  
> X-Postfix-Queue-ID: A8028C0619  
> X-Postfix-Sender: rfc822; giannoug@localhost  
> Arrival-Date: Mon, 4 Aug 2008 16:37:11 +0300 (EEST)
> 
> Final-Recipient: rfc822; giannoug@_youporn_.com  
> Action: failed  
> Status: 5.7.1  
> Remote-MTA: dns; gmail-smtp-in.l.google.com  
> Diagnostic-Code: smtp; 550-5.7.1 [77.49.112.75] The IP you&#8217;re using to send  
> mail is not authorized 550-5.7.1 to send email directly to our servers.  
> Please use the SMTP 550-5.7.1 relay at your service provider instead. Learn  
> more at 550 5.7.1  
> http://mail.google.com/support/bin/answer.py?answer=10336 d4si6005819fga.8

Δώσε βάση στα **bold** και _italic_ και όχι στο e-mail από το οποίο και στο οποίο προσπάθησα να στείλω 😛

Λέει ότι πρέπει να κάνεις relay τα email στον SMTP του ISP σου. Εδώ μπορεί να μπερδευτεί κάποιος..  
Ποιόν SMTP βάζω?? Εγώ, συνδρομητής Forthnet, έβαλα mailgate.forthnet.gr. Με, πραγματικά, λίγο ψάξιμο που έκανα, βρήκα ότι σε κάθε ISP βάζεις τον αντίστοιχο SMTP που χρησιμοποιείς για τα email του ISP (στο Outlook / Thunderbird κτλ). Testing will tell.

Μια λίστα για όσους βαριούνται, τους καταλαβαίνω απόλυτα:  
_(προφανώς δεν τα έχω δοκιμάσει όλα)_  
**Forthnet**: mailgate.forthnet.gr  
**ONTelecoms**: smtp.ontelecoms.gr  
**OTENET**: mailgate.otenet.gr  
**HOL**: mail.hol.gr  
**Tellas**: smtp.tellas.gr

Μην δοκιμάσεις να βάλεις SMTP άλλης εταιρίας γιατί συνήθως είναι ρυθμισμένοι να δέχονται email μόνο απ&#8217; τις IP των πελατών τους.

Δεν είσαι βέβαια αναγκασμένος να βάλεις αυτόν τον SMTP. Εάν έχεις κάποιο server κάπου αλλού, μπορείς να κάνεις relay μέσω αυτού τα email σου. Μπορείς επίσης να χρησιμοποιήσεις και το GMail σου, αλλά παλιά που το είχα ψάξει, βρήκα ότι ήθελε να ξανακάνεις compile τον MTA για SSL και αρλούμπες..

Το πως, τώρα, θα τα βάλεις. Δεν μπορώ να βοηθήσω γιατί δεν είναι για όλους τους MTA ίδιο. Πάρε κάποια query στο Google που μπορεί να βοηθήσουν όμως!

**Για Postfix**: <http://www.google.com/search?q=smtp+relay+postfix>  
Άντε και επειδή είμαι καλός [κoίτα και εδώ](http://www.gungeralv.org/notes/archives/2003/06/howto_configure_postfix_to_use_a_remote_smtp_relay_host.php) 😛  
**Για QMail**: <http://www.google.com/search?q=smtp+relay+qmail>  
**Για sendmail**: <http://www.google.com/search?q=smtp+relay+sendmail>  
Τι καλοσύνη είναι [αυτή](http://cri.ch/linux/docs/sk0009.html) σήμερα ρε!

Αυτά.  
Το post αυτό, μαζί με ένα άλλο, παίζει να υπάρχουν μήνες στα draft. Ούτε εγώ θυμάμαι πότε το ξεκίνησα! 😛
