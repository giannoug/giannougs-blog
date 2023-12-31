---
title: How ye bury yer treasure?
date: 2012-06-17T17:16:15+00:00
url: /how-ye-bury-yer-treasure/
cover:
    image: how-ye-bury-yer-treasure.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - backup
  - dropbox
  - duplicity
  - duply
  - vps

---
Πώς προστατεύω τα πολύτιμα αρχεία μου; Που τα τοποθετώ και πώς τα μεταφέρω εκεί με ασφάλεια; Κι αν κάποιος ανακαλύψει την κρυψώνα μου; Τι θα συμβεί τότε; Θα παραμείνουν προστατευμένα ή θα μου τα καταστρέψουν/λεηλατήσουν; Προβληματισμοί σαν αυτούς βασανίζουν το μυαλό όλων των φρόνιμων system administrators και users. Κι όχι μόνο: Παρόμοιους είχαν οι πειρατές της Καραϊβικής, όπως κι εκείνοι των θρυλικών παιχνιδιών του Monkey Island. Αλλά ας μην ξεφεύγουμε.

Ένα από τα μεγαλύτερα προβλήματα των admins είναι τo backup — ή τουλάχιστον έτσι θα έπρεπε. Στα τεύχη 005 και 006 του deltaHacker είδαμε πώς μπορούμε ν’ αγοράσουμε και να σετάρουμε το δικό μας VPS, από την αρχή μέχρι το τέλος. Δεν είπαμε ωστόσο τίποτα για το backup, ενώ στην πραγματικότητα θα μπορούσαμε να πούμε πολλά.

Μη νομίζετε ότι το backup είναι πάντα μια απλή εργασία. Από τη σωστή λήψη και τήρηση έως και τη διαχείρισή του, απαιτείται αρκετή δουλειά. Ποτέ δεν είναι αρκετό ένα backup και (σχεδόν) πάντα θα υπάρξει κάποιο πρόβλημα, είτε κατά τη διαδικασία επαναφοράς είτε κατά την αποθήκευση στα διάφορα filesystem. Επίσης, το πρόβλημα του backup δεν απασχολεί μόνο τους διαχειριστές συστημάτων. Αποτελεί σημαντικό ζήτημα για \*κάθε\* χρήστη, τουλάχιστον για όσους δίνουν αξία στα αρχεία και στη δουλειά τους και (σοφά) δεν εμπιστεύονται στο 100% το hardware του υπολογιστή.

Σ’ αυτό το άρθρο δείχνουμε πώς μπορούμε να έχουμε \*πάντα\* ασφαλή κι αξιόπιστα backup, απλά και γρήγορα. Η λύση που παρουσιάζουμε εφαρμόζεται σε συστήματα Linux, BSD κι άλλα Unixοδειδή, όπως είναι το OS X. Μερικές βασικές χρήσεις που μπορούμε να σκεφτούμε είναι η τήρηση backup του site μας σ’ ένα άλλο μηχάνημα (ενδεχομένως VPS), η τήρηση backup του Dropbox folder σ’ έναν τοπικό ή απομακρυσμένο fileserver που δεν υποστηρίζει το Dropbox κ.ά.

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2012/06/12/deltahacker009/" title="deltaHacker 009 — El Pollo Diablo Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker Ιουνίου (τεύχος 009)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και security που δεν κυκλοφορεί στα περίπτερα και απευθύνεται σε όλους, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.