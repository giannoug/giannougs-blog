---
title: Setάροντας έναν VPS. Επεισόδιο 3ον.
date: 2009-08-13T11:57:03+00:00
url: /setarontas-enan-vps-part-iii/
categories:
  - How-to και άλλα
tags:
  - guide
  - server
  - Setάροντας έναν VPS
  - ubuntu
  - vps

---
Μετά από δσδαφ.. από σφααφ.. χμμ.. Μετά από.. Πολλούς και βάλε μήνες έρχεται το 3ο άρθρο στη σειρά &#8220;**Setάροντας έναν VPS.**Ubuntu και **όχι** σε **Debian**. Η αλλαγή αξίζει, τράστ μι. Δεν αλλάζει τίποτα το σημαντικό, απλά τα Ubuntu είναι λίγο πιο.. προσεγμένα σε κάποια σημεία. Α και ποιό active στο development!

Σε αυτό το άρθρο θα βάλουμε email server (Postfix) και dns server (Bind9)!

Ας ξεκινήσουμε με Postfix. Δεν θυμάμαι αν το είπα, αλλά δεν θα γράψω πως στήσεις virtual domain κτλ. Βάζουμε mail server μόνο και μόνο για να στέλνουμε mail απ&#8217; την PHP (WordPress, SMF, Joomla, mail()). Εξάλλου ο οδηγός απευθύνετε σε VPS (max 512Mb, άντε 1Gb RAM) 😉  


{{< highlight bash >}}
apt-get install postfix
{{< / highlight >}}

Κούραση ε; Τελειώσαμε 😛  
**Σημείωση 1:** Η PHP έχει σαν default SMTP το Sendmail, δεν χρειάζεται να το αλλάξουμε αφού ο Postfix υποστηρίζει τα &#8220;κόλπα&#8221; του Sendmail.  
**Σημείωση 2:** Για Ubuntu είμαι **σίγουρος** δε θέλει **κανένα** tweak στο php.ini, για Debian **νομίζω** θέλει. Δεν μπορώ να βοηθήσω παραπάνω. Πάει καιρός απ&#8217; τα Debian 😀

Πάμε και Bind, εδώ έχει ζουμί η υπόθεση αλλά και διάβασμα πολύ.

Κλασικά κάνουμε εγκατάσταση τον bind.. **Προσοχή!** Το package είναι το **Bind9**! Υπάρχει και package bind αλλά έχει κάποιες διαφορές απ&#8217; το bind9..

{{< highlight bash >}}
apt-get install bind9
{{< / highlight >}}

Με τον bind μπορούμε να φιλοξενούμε το dns του domain μας, τα A, CNAME, MX κτλ records των domain.

Καταρχάς πρέπει να φτιάξουμε ένα αρχείο που θα περιέχει τα records του domain. Με Googling σε διάφορα site έχω καταλήξει σε αυτές τις ρυθμίσεις. Δεν ξέρω αν είναι σωστές, το σίγουρο είναι ότι δουλεύουν πάντως! Βάλ&#8217; τες σε ένα αρχείο με όνομα db.example.com, όπου example.com βάζεις το domain σου. Δεν παίζει ρόλο το όνομα, απλά για να τα ξεχωρίζεις!

{{< highlight dns >}}
;  
; giannoug&#8217;s sample bind dns records file.  
;  
$TTL 3600  
@ IN SOA ns1.example.com. hostmaster.example.com. (  
00001 ; Serial  
10800 ; Refresh  
3600 ; Retry  
604800 ; Expire  
86400 ) ; Negative Cache TTL

IN NS ns1.example.com.  
IN NS ns2.example.com.  
IN NS ns3.example.com.  
IN NS ns4.example.com.

IN A 10.0.0.1

IN MX 10 example.com

ns1 IN A 10.0.0.1  
ns2 IN A 10.0.0.2  
ns3 IN A 10.0.0.3  
ns4 IN A 10.0.0.4

www IN A 10.0.0.1  
sub IN A 10.0.0.5  
{{< / highlight >}}

Χρειάζεται τις κατάλληλες τροποποιήσεις, δεν αναλύω τι και που, αφού διαβάζεις το άρθρο ξέρεις τι πρέπει να φτιάξεις! Μη ξεχνάς το Serial του domain πρέπει να αλλάζει κάθε φορά που πειράζεις τα record του domain! Συνήθως βάζουν ημερομηνία ή unix epoch time αλλά εγώ πρωτοτυπώ 😛

Αφού λοιπόν τα φτιάξουμε όλα, πρέπει να βάλουμε ακομα ένα.. ας το πούμε reference στο αρχείο με τα record του domain. Οι γραμμές που πρέπει να τοποθετηθούν είναι..

{{< highlight dns >}}
zone "example.com" {  
type master;  
file "/etc/bind/db.example.com";  
allow-transfer {10.0.0.1; 10.0.0.2; 10.0.0.3};  
};  
{{< / highlight >}}

..στο αρχείο _named.conf.local_ (που μη ξεχνάς βρίσκεται στο /etc/bind)!

Αυτά για την ώρα! 🙂