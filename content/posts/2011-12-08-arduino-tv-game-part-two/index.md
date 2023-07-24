---
title: Το δικό σας TV-Game με το Arduino, μέρος 2 από 2
date: 2011-12-08T18:56:30+00:00
url: /arduino-tv-game-part-two/
cover:
    image: arduino-tv-game-part-two.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - arduino
  - arduino tv-game
  - avr

---
Στο προηγούμενο τεύχος μετατρέψαμε το Arduino σε μια αρκετά απλή, αλλά λειτουργική κονσόλα παιχνιδιών. Τα βήματα που ακολουθήσαμε αφορούσαν στο σχηματισμό του hardware, ενώ δεν έλειψαν και οι απαραίτητες δοκιμές. Αυτή τη φορά, έχοντας έτοιμα τα πάντα, θα γράψουμε ένα απλό παιχνιδάκι για την κονσόλα μας!

Πριν ξεκινήσουμε το όλο εγχείρημα, έπρεπε να αποφασίσουμε ποιο παιχνίδι θα υλοποιήσουμε. Υπάρχουν πολλά παιχνιδάκια που θα μπορούσε να τρέξει μια κονσόλα με το Arduino. Σχεδόν όλα ωστόσο, απαιτούν προχωρημένες γνώσεις στον τομέα του game development και ξεφεύγουν κατά πολύ από τον σκοπό του άρθρου. Έτσι, αποφασίσαμε να στραφούμε σε κάτι απλό. Μήπως υπάρχει κανένας που δυσαρεστήθηκε θεωρώντας ότι δεν θα γράψουμε κώδικα; Αν υπάρχει, μάλλον βιάστηκε! Το απλό παιχνιδάκι που θα φτιάξουμε έχει και κώδικα, έχει και την απαραίτητη απλότητα, ώστε να μπορούμε στο μέλλον να το επεκτείνουμε. Ας δούμε λοιπόν τι έχουμε στη διάθεσή μας. Το hardware περιλαμβάνει δύο κουμπιά και μια έξοδο ασπρόμαυρου, αναλογικού σήματος, χαμηλής ανάλυσης. Επομένως, το πιο ταιριαστό παιχνίδι είναι ένα κουίζ ερωτήσεων-απαντήσεων. Σκεφτείτε κάτι σαν το trivial, χωρίς τα ζάρια, αλλά με όλο το χαβαλέ μεταξύ των αντιπάλων 😉 Παιχνίδια αυτού του είδους υπάρχουν για όλες τις κονσόλες και είναι δημοφιλή στις μεγάλες παρέες. Βέβαια, το δικό μας θα έχει σίγουρα λιγότερες ερωτήσεις, ενώ θα του λείπουν και εντυπωσιακά εφέ. Όλα αυτά όμως είναι λεπτομέρειες, αφού θα το έχουμε φτιάξει εξ ολοκλήρου μόνοι μας!

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2011/12/07/deltahacker003/" title="deltaHacker 003 – Πρωινή Μπουγάτσα edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker Δεκεμβρίου (τεύχος 003)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και infosec που δεν κυκλοφορεί στα περίπτερα, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.