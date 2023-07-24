---
title: Εγκατάσταση Webmin σε Ubuntu Linux
date: 2008-10-06T14:00:47+00:00
url: /egkatastasi-webmin-ubuntu/
categories:
  - How-to και άλλα
tags:
  - ubuntu
  - webmin

---
Αν και τα βήματα που θα δώσω είναι δοκιμασμένα (τώρα θα το κάνω εγκατάσταση σε ένα Virtual-PC) σε Ubuntu Server 8.04, υπάρχει πιθανότητα να θέλουν κάποιες μικρο-αλλαγές. Για παράδειγμα τα Ubuntu Server θέλουν να εγκαταστήσεις την Perl για να δουλέψει το Webmin. Τα Debian ή γενικά κάποια άλλη παραλλαγή, μπορεί να την έχουν ήδη εγκατεστημένη ή να διαφέρουν λίγο τα packages στα repositories.  

Υπάρχουν 2 τρόποι εγκατάστασης του Webmin. Ο πρώτος τρόπος είναι απλά περνώντας το .deb που κατεβάζεις από το site του Webmin, ενώ ο δεύτερος βάζοντας το repository του Webmin και εγκαθιστώντας το απλά με ένα **sudo apt-get install webmin**. Το καλό του δεύτερου τρόπου είναι ότι γίνεται update μαζί με όλο το σύστημα (apt-get upgrade), ενώ το κακό του είναι ότι δεν το έχω δοκιμάσει 😛

Ίσως το Webmin υπάρχει στα repo των Ubuntu, αλλά δεν το έχω ψάξει.

#### Εγκατάσταση .deb από Webmin.com

**Βήμα 1**:  
```
root@Slave-PC:~$ wget <em>και_το_link_της_έκδοσης</em>
``` 
Αρχικά (προφανώς 😛 ) κατεβάζεις το package (.deb) με το [wget](http://en.wikipedia.org/wiki/Wget). Δεν έχει σημασία που, αρκεί να έχεις δικαιώματα να γράψεις αρχεία εκεί 😉 Συνήθως στο /home σου τα κάνεις και μετά.. σκουπίζεις 😛

**Βήμα 2**:  
```
root@Slave-PC:~$ apt-get install libnet-ssleay-perl openssl libauthen-pam-perl libio-pty-perl libmd5-perl
```  
Με αυτή την εντολή βάζεις όλα τα packages που χρειάζονται για την λειτουργία του Webmin. Είναι όλα για την Perl.  
**Note**: Αν δεν κάνεις αυτό το βήμα και προχωρήσεις με την εγκατάσταση του Webmin (Βήμα 3) θα σου ζητηθούν αυτά τα packages με μια εντολή (γαμώ δεν την θυμάμαι..) να τα βάλει και να συνεχίσει με το Webmin. Δεν χάνεις πάντως τίποτα να δοκιμάσεις.. και να μου πεις 😛

**Βήμα 3**:  
```
root@Slave-PC:~$ dpkg -i webmin_1.430_all.deb
```  
Και αυτό ήτανεεε.. (τύφλα να έχει το 5 minute install του WordPress).

#### Εγκατάσταση μέσω repository του Webmin

**Note**: ΔΕΝ το έχω δοκιμάσει. Απλά υποθετικά τι θα έκανα εγώ, γράφω.

Βήμα 1α:  
```
root@Slave-PC:~$ nano /etc/apt/sources.list
```  
Για να βάλεις το repo στην λίστα με τα repo του APT.

```
deb http://download.webmin.com/download/repository sarge contrib
```  
Αυτό το βάζεις μέσα στο sources.list (που άνοιξες με το nano πριν λίγο).

Βήμα 2β:  
```
root@Slave-PC:~$ wget http://www.webmin.com/jcameron-key.asc
```  
Για να κατεβάσουμε το GPG key του μάστορα, αλλιώς δεν μπορείς να κατεβάσεις απ&#8217; το repo του.  
Επίσης τρέχουμε..  
```
root@Slave-PC:~$ apt-key add jcameron-key.asc
```  
..για να το περάσουμε 😉

Βήμα 2:  
```
root@Slave-PC:~$ apt-get update
```  
Πρώτα κάνουμε update τα πακετάκια μας απ&#8217; τα repo..  
```
root@Slave-PC:~$ apt-get install webmin
```  
..μετά εγκατάσταση 😉

Τώρα πηγαίνοντας στο http://_ip\_tou\_masiniou_:10000 έχουμε στην διάθεσή μας σχεδόν όλες τις ρυθμίσεις του server / pc μας 😉

Αυτό ήταν, δεκτές όλες οι γνώμες.

19/12/08: Το πέρασα ένα facelift 😛  
22/12/08: Έβαλα και το GPG Key γιατί αλλιώς δεν μπορείς να κατεβάσεις απ&#8217; το repo του Webmin.
