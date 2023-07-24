---
title: Εγκατάσταση Vista στο Asus EEE PC 1000H
date: 2009-02-15T17:27:34+00:00
url: /egkatastasi-vista-sto-eee-pc-1000h/
categories:
  - How-to και άλλα
tags:
  - eee pc
  - eee pc 1000h
  - format
  - vista
  - windows

---
Προχτές (που λέει ο λόγος) χρειάστηκε να περάσω Vista (imo είναι καλύτερα απ&#8217; τα XP) μιας και κανένα Linux distro δεν έκατσε καλά. Οι λόγοι πολλοί και διάφοροι αλλά θα τους αναφέρω στον επόμενο οδηγό. Για την ώρα ας βάλουμε Windows 😛

Καταρχάς πρέπει να πετσοκόψουμε λίγο το DVD επειδή δεν έχουνε όλοι μεγάλα flashάκια (με ένα 4Gb που δοκίμασα δεν χωρούσαν για 300mb) και επειδή βάζει κάποια features **-λίγο-** άχρηστα μέσα. Flashάκι γιατί το EEE PC **δεν** έχει DVD drive. _Πετσοκόψιμο_ μπορείς να κάνεις και στα XP/Vista που βάζεις στο desktop σου. Απλά χρειάζεσαι το [nLite](http://www.nliteos.com/) που είναι για XP ή το [vLite](http://www.vlite.net/) για Vista. Το πως δεν θα το εξηγήσω, είναι αρκετά [απλό](http://www.google.com/search?q=vlite+how+to) 😉  


Αφού λοιπόν φτιάξουμε το installation πρέπει και να ετοιμάσουμε το flashάκι. Ανοίγουμε cmd και γράφουμε..

```
C:\Users\giannoug>diskpart
```

Αφού ανοίξει, έχει ένα σπαστικό delay στην αρχή, γράφουμε τις εντολές παρακάτω **μια-μια** (one by one).

```
LIST DISK
SELECT DISK <em>νούμερο_flash</em>
CLEAN
CREATE PARTITION PRIMARY
SELECT PARTITION 1
ACTIVE
FORMAT FS=32
ASSIGN
EXIT
```

Μερικές εντολές για το diskpart είναι άχρηστες. Για παράδειγμα το CREATE PARTITION 1 και το FORMAT FS=32 δεν χρειάζονται, αφού όλα τα flashάκια έχουνε partition και στο κάτω-κάτω μπορεί να μην θες να το κάνεις format. Εάν επιλέξεις να παραβλέψεις όλες τις εντολές δεν θα bootάρει. Δοκίμασε μόνο την ACTIVE (θέλει και κάποιες απ&#8217; τις παραπάνω για να επιλέξεις το partition) αν θες να πειραματιστείς. Εγώ βιαζόμουν και δεν το έψαξα 😛

<p class="alert">
  Πιστεύω να θυμάσαι ότι όταν κάνεις format χάνονται <strong>όλα</strong> τα δεδομένα απ&#8217; το partition του σκληρού!
</p>

Αφού τελειώσουμε με αυτό, πάμε στον φάκελο με το custom installation και.. μεταφέρουμε **απλά** τα αρχεία στο flashάκι! Το μόνο που μένει είναι να ενεργοποιήσουμε να bootάρει απ&#8217; το flashάκι στο BIOS του EEE 😉 Να προσθέσω πως είναι ένας καλός τρόπος να κάνεις format σε όλα τα PC. Γιατί? Γιατί είναι **αρκετά** γρήγορο 😉

Αφού φτιάξεις την ρύθμιση στο BIOS και αν όλα πάνε καλά θα bootάρει. Από εκεί και πέρα όλα γνωστά, [πιστεύω](http://www.google.com/search?q=how+to+install+vista). Αφού τελειώσει το format χρειάζεται drivers. Πριν αρχίσεις να κοσκινίζεις το Google και τα διάφορα forum που βρίσκεις για τους drivers, να πω πως η κάμερα, το bluetooth και η ο ήχος δεν θέλουν να περάσεις κάποιον extra driver για να δουλέψουν. Πιο συγκεκριμένα, για την κάμερα δεν βρήκα, ούτε για το bluetooth. Δεν υπάρχουν ούτε για XP. Δουλεύουν με τους drivers που έχουνε τα Vista όμως. Για τον ήχο υπάρχει driver και ένα προγραμματάκι. Λογικά θα θες να τα περάσεις αφού για να υπάρχουν είναι καλύτερα απ&#8217; των Vista 😛

Οι drivers που θα χρειαστείς είναι..  
_Τα link είναι για τις τελευταίες εκδόσεις, πάντα._

> **Για γραφικά:**  
> Intel GMA950  
> [Download](http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=2300&DwnldID=16312&strOSs=156&OSFullName=Windows%20Vista*%20Ultimate,%2032-bit%20version&lang=eng)
> 
> <p style="display: block">
>   <strong>Για chipset:</strong><br /> Mobile Intel® 945 Express Chipset Family<br /> <a href="http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&#038;ProductID=2300&#038;DwnldID=16023&#038;strOSs=All&#038;OSFullName=All%20Operating%20Systems&#038;lang=eng">Download</a>
> </p>
> 
> **Για touchpad (απίστευτος driver!):**  
> [Download](http://www.emc.com.tw/eng/st_tpn_sp.asp)
> 
> **Για ήχο:**  
> Απ&#8217; το site της Asus, για τα XP.  
> <a href="http://support.asus.com/download/download.aspx" class="broken_link" rel="nofollow">Download</a>
> 
> **Για Wired LAN (Ethernet):**  
> Atheros AR81 Family  
> <a href="http://partner.atheros.com/Drivers.aspx" class="broken_link" rel="nofollow">Download</a>
> 
> **Για Wireless LAN:**  
> RaLink RT2860  
> [Download](http://www.ralinktech.com/ralink/Home/Support/Windows.html)
> 
> **Για ACPI:**  
> Αυτός είναι για Vista. Ο official έχει πρόβλημα.  
> <a href="http://gekko.me/acpi.php" class="broken_link" rel="nofollow">Download</a>

Αυτά για την ώρα 😉
