---
title: Γνωριμία με το AWMN
date: 2014-01-30T19:58:20+00:00
url: /gnorimia-awmn/
cover:
    image: gnorimia-me-to-awmn.jpg
categories:
  - deltaHacker
tags:
  - 802.11
  - awmn
  - wifi
  - wireless
  - wlan

---
Πώς θα σας φαινόταν η σύνδεση σε ένα τεράστιο, ασύρματο LAN; Η αλήθεια είναι ότι, όσο τεράστιο κι αν είναι ένα τέτοιο δίκτυο, δεν θα βρούμε τίποτα εκεί που να μην παρέχεται στο Internet. Ωστόσο, μια περιορισμένη δικτυακή κοινότητα αποτελεί πρόσφορο έδαφος για την ανταλλαγή μουσικής, ταινιών, τηλεοπτικών σειρών κι άλλων δεδομένων. Επίσης, για εμάς τουλάχιστον, ένα μεγάλο LAN αποτελεί άλλο ένα &#8230;μεγάλο παιχνίδι. Από τη στιγμή που διαβάζετε deltaHacker, πιστεύουμε ότι το ίδιο ισχύει και για εσάς 🙂

Γύρω στο 2002, όταν το γρήγορο Internet έκανε τα πρώτα του δειλά βήματα, μια ομάδα αποφάσισε να δημιουργήσει κάτι πιο σταθερό και φυσικά γρηγορότερο. Κάπως έτσι ξεκίνησε το Athens Wireless Metropolitan Network (δεν υφίσταται μόνο στην Αθήνα), το οποίο μέσα σε λίγους μήνες κατάφερε να συγκεντρώσει πάρα πολλούς χρήστες. Παρόλο που αρχικά ξεκίνησε ως ένας εναλλακτικός πάροχος broadband, τελικά κατέληξε να λειτουργεί παράλληλα με τους παρόχους Internet, χωρίς όμως να θέλει να τους αντικαταστήσει. Το δίκτυο του AWMN λειτουργεί ακόμη και σήμερα, χωρίς να είναι πλέον τόσο ενεργό αλλά χωρίς και να έχει απονεκρωθεί. Σε αυτό το άρθρο θα δούμε τα βασικά χαρακτηριστικά του AWMN και θα μιλήσουμε για τον τρόπο λειτουργίας του, χωρίς να εισέλθουμε σε \*πολλές\* τεχνικές λεπτομέρειες. Φυσικά θα δούμε πώς μπορούμε να συνδεθούμε κι εμείς σε αυτό, όπως επίσης και τα όσα μπορεί να μας προσφέρει! Ένα θετικό στοιχείο του εγχειρήματος, πέρα από την ευκαιρία για πειραματισμό και παιχνίδι με τον ασύρματο εξοπλισμό, είναι το πολύ χαμηλό κόστος. Το μόνο που θα χρειαστούμε είναι μια \*καλή\* κεραία WiFi.

## Ένδον του AWMN

Πριν ξεκινήσουμε τις ασύρματες περιπέτειες, θα ήταν καλό να γνωρίζουμε τις αρχές λειτουργίας του μητροπολιτικού δικτύου. Αυτό θα μας βοηθήσει τόσο στη σύνδεση, όσο και στην παραμονή στο δίκτυο. Θα ξεκινήσουμε με τη διάρθρωσή του. Το AWMN απαρτίζεται από ασύρματους κόμβους που χωρίζονται σε δύο κατηγορίες. Ένας κόμβος μπορεί να αποτελεί τμήμα της «ραχοκοκαλιάς» του δικτύου (backbone) ή έναν απλό τερματικό σταθμό, στον οποίο συνδέονται χρήστες. Με άλλα λόγια, ένας κόμβος μπορεί είτε να διαβιβάζει δεδομένα μεταξύ άλλων κόμβων είτε να μεταφέρει πακέτα από το δίκτυο από και προς κάποιον χρήστη. Ένας κόμβος backbone, όμως, μπορεί να λειτουργεί \*και\* σαν access point, ώστε να συνδέονται πάνω του απλοί χρήστες. Αυτή η δικτυακή τοπολογία ονομάζεται «partial mesh». Τα δύο διαφορετικά είδη κόμβων χρησιμοποιούν διαφορετικές τεχνολογίες. Για παράδειγμα, οι κόμβοι backbone χρησιμοποιούν το πρωτόκολλο 802.11b, ενώ οι κόμβοι που λειτουργούν σαν access points χρησιμοποιούν το 802.11g και σπανιότερα το 802.11n. Επιπλέον, εκτός από διαφορετικά πρωτόκολλα χρησιμοποιούνται και διαφορετικές κεραίες, με σκοπό τη βελτιστοποίηση της απόδοσης. Συγκεκριμένα, οι κόμβοι backbone χρησιμοποιούν ισχυρά κατευθυντικές κεραίες, καθώς εκπέμπουν μόνο προς έναν άλλο κόμβο και κατ&#8217; επέκταση προς μια συγκεκριμένη τοποθεσία. Αντίθετα, οι κόμβοι τύπου access point χρησιμοποιούν &#8220;πανκατευθυντικές&#8221; κεραίες (omnidirectional), αφού το σήμα εκπομπής τους πρέπει να λαμβάνεται από όσο το δυνατόν περισσότερους χρήστες.

Όπως καταλαβαίνετε, ένας απλός client του AWMN χρειάζεται αρκετά απλό εξοπλισμό (κάρτα WiFi και μια σχετικά ισχυρή κεραία). Τι γίνεται όμως με το software; Φυσικά, στο AWMN δεν επικρατεί αναρχία. Αντιθέτως, πρόκειται για ένα αυστηρά δομημένο κι ελεγχόμενο δίκτυο. Αν ο καθένας έκανε ό,τι θεωρούσε σωστό, δε θα δούλευε απολύτως τίποτα 😀 [Σ.τ.Ε. from the subtle-political-messages department] Το AWMN χρησιμοποιεί τις διευθύνσεις στο subnet 10.0.0.0/8 κι αυτό κυρίως για να μη εμπλέκεται στα υπόλοιπα δίκτυα και στο Internet. Η \*σωστή\* διευθυνσιοδότηση εντός του δικτύου, όπως επίσης και ο γενικότερος έλεγχος της λειτουργίας του, πραγματοποιούνται από το WiND. Το WiND δεν είναι τίποτε άλλο παρά μια εφαρμογή γραμμένη σε PHP, η οποία γνωρίζει τις διευθύνσεις όλων των κόμβων, όπως επίσης και τις υπηρεσίες που προσφέρει ο καθένας. Με άλλα λόγια, αν κάποιος κόμβος δεν υπάρχει στα μητρώα του WiND, είναι σα να μην υπάρχει καθόλου στο δίκτυο! Το WiND μπορεί να χρησιμοποιηθεί από οποιονδήποτε και αποτελεί λογισμικό ανοιχτού κώδικα. Για την ακρίβεια, το χρησιμοποιούν όλες οι ασύρματες κοινότητες στην Ελλάδα! Την εκδοχή του WiND που προορίζεται για το AWMN μπορούμε να την βρούμε στο http://wind.awmn.net (μέσω Internet) καθώς και στο http://wind.awmn (μέσω του ασύρματου δικτύου).

> Διαβάστε ολόκληρο το άρθρο στο <a href="http://deltahacker.gr/2013/10/27/deltahacker025/" title="deltaHacker 025 - Temporal Distortion Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker 025 (τεύχος Οκτωβρίου 2013)</a>.
