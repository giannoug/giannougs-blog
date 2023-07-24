---
title: OpenWRT και Squid cache.
date: 2010-05-11T15:54:54+00:00
url: /openwrt-squid-server/
cover:
  image: Screenshot-20100511-180534.png
categories:
  - How-to και άλλα
tags:
  - cache
  - linux
  - networking
  - openwrt
  - squid
  - ubuntu

---
Το [OpenWRT](http://openwrt.org/) είναι μια διανομή Linux για router. Τι καλύτερο απ&#8217; το να μπορείς να πειράξεις τα πάντα στο router σου; Ακόμα και κάποιες ρυθμίσεις τις οποίες με το stock firmware δεν μπορείς; Δεν είναι η μόνη διανομή για router γενικά, αλλά είναι η μόνη που δουλεύει στο router μου. Όπως είπα με το OpenWRT μπορείς να πειράξεις -σχεδόν- τα πάντα 😉 Λοιπόν&#8230;  


Τι θα γινόταν αν κάναμε redirect όλο το traffic της port 80 στον Squid cache του δικτύου; Εκτός απ&#8217; το ότι θα αναβοσβήνουν σαν τρελά όλα τα λαμπάκια του switch, θα γλιτώσουμε να ρυθμίσουμε όλους τους browser να χρησιμοποιούν τον cache! Ακόμα όλες οι συσκευές, κινητά, laptop κτλ θα μπορούν να χρησιμοποιούν τον proxy. Το πως μπορείς να περάσεις το OpenWRT στο router είναι άλλη και μεγάλη ιστορία. Δεν θα ασχοληθώ γιατί δεν ξέρω και πολλά, αλλά το κύριο site της διανομής έχει πολλές πληροφορίες. Δεν χρειάζεται να είναι σόνι και καλά OpenWRT το router, οποιαδήποτε Linux διανομή μας κάνει (ρουτερόπισο κανείς;). Το ίδιο ισχύει και για τον Squid server φυσικά.

Καταρχάς πρέπει να στήσουμε τον Squid σε κάποιο μηχάνημα. Εγώ τον τρέχω σε Ubuntu 10.4 και η εγκατάσταση γίνεται με ένα απλό πακέτο με τον αγαπημένο σου package manager. Μιας και δεν έχω GUI, πάμε με console.

```
  apt-get install squid
```

Τέλος, πρέπει να πας στο config του, που βρίσκεται στο _/etc/squid/squid.conf_, να βρεις το directive http_port και να βάλεις ένα transpart δίπλα. Κάτι σαν αυτό:

```
  http_port 3128 transparent
```

Υπάρχουν κιάλλες ρυθμίσεις που μπορείς να πειράξεις, αλλά ίσως ασχοληθώ άλλη φορά με αυτές. Πάμε στο router τώρα&#8230; Αφού συνδεθείς μέσω SSH θα πρέπει να δημιουργήσεις ένα αρχείο που περιέχει κάποιες routing εντολές για το iptables. Δεν έχει σημασία που, εγώ στο OpenWRT τα έβαλα στο _/etc_, χύμα, με όνομα squid. Το αρχείο θα πρέπει να περιέχει:

```
#!/bin/sh
LANIF=br-lan #LAN interface
ROUTER=192.168.1.1 #Router's IP
INTERCEPT_PORT=80 #What port you want to intercept
TO=192.168.1.100 #Target's IP, ie the system running the transparent proxy -- it doesn't even need to be in the local network!
TO_PORT=3128 #Target port
echo "Loading intercept rules for port $INTERCEPT_PORT to $TO:$TO_PORT"
# Coming from non-target lan address to port, rewrite destination to target
iptables -t nat -A prerouting_lan -s ! $TO -p tcp --dport $INTERCEPT_PORT -j DNAT --to $TO:$TO_PORT
# Going to the target from the lan, rewrite source as router
iptables -t nat -A postrouting_rule -o $LANIF -d $TO -p tcp --dport $TO_PORT -j SNAT --to $ROUTER
# Allow forwarding on lan to the target
iptables -A forwarding_lan -d $TO -p tcp --dport $TO_PORT -j ACCEPT
```

Φυσικά χρειάζεται τις κατάλληλες αλλαγές. Τώρα θα πρέπει να το τρέχουμε κάπως, είτε με το χέρι κάθε φορά που κάνουμε restart το router, είτε με κάποιο script αυτόματα. Ο καλύτερος τρόπος είναι αυτόματα με το firewall του OpenWRT. Μπορείς να πας στο _/etc/config/firewall_ και να προσθέσεις στο τέλος:

```
config 'include'
        option 'path' '/etc/squid'
```

Αυτό ήταν&#8230; Όλο το traffic της port 80 πάει μέσα απ&#8217; τον cache server του δικτύου! Δεν το έχω ψάξει πολύ, ίσως γίνεται με καλύτερο τρόπο, αλλά δούλευει! Την τελευταία βδομάδα τουλάχιστον&#8230; 😛
