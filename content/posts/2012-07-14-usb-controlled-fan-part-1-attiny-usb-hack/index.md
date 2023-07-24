---
title: Βάλτε μυαλό στον ανεμιστήρα, part 1 (ATtiny USB hack)
date: 2012-07-14T11:04:17+00:00
url: /usb-controlled-fan-part-1-attiny-usb-hack/
cover:
    image: usb-controlled-fan-part-1-attiny-usb-hack.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - arduino
  - attiny
  - avr
  - usb fan

---
Τα καταστήματα που πουλάνε δώρα είναι γεμάτα με συσκευές USB. Μιλάμε για USB gadgets σαν αυτά που κρατάνε ζεστή την κούπα του καφέ, φωτίζουν το πληκτρολόγιο, κάνουν αέρα και δεν συμμαζεύεται! Αυτές οι συσκευές μπορούν να κάνουν οποιοδήποτε geek χαρούμενο. Μπορούν όμως και να το απογοητεύσουν λίγο, αφού δεν αλληλεπιδρούν καθόλου με το λογισμικό του υπολογιστή. Ε, λοιπόν, εμείς αποφασίσαμε ν” αλλάξουμε αυτή την κατάσταση, αναβαθμίζοντας για αρχή ένα μικρό ανεμιστηράκι 🙂

Πριν από μερικά χρόνια, ο γράφων δέχτηκε δωράκι έναν ανεμιστήρα USB. Ο ανεμιστήρας κάνει άψογα την δουλειά του ακόμα και σήμερα, αλλά όπως τα περισσότερα USB gadgets δεν γίνεται αντιληπτός από το λειτουργικό σύστημα του υπολογιστή. Το μόνο που κάνει είναι να τραβάει ρεύμα από τη θύρα USB και να λειτουργεί αδιάκοπα, μέχρι να πατήσει κάποιος τον ενσωματωμένο διακόπτη (ή να τραβήξει το καλώδιο από τη θύρα). Με τη βοήθεια ενός κατσαβιδιού και μετά από μια σύντομη έρευνα, ανακάλυψε ο γράφων ότι ο ανεμιστήρας έχει υπεραρκετό χώρο στο εσωτερικό του για την προσθήκη ηλεκτρονικών. Κάπως έτσι άρχισαν να περνάνε διάφορες ιδέες από το μυαλό. Ο ανεμιστήρας είναι εντελώς χαζός και θα ήταν ενδιαφέρον αν είχε κάποιο είδος ευφυΐας! Δεν θα “χε πλάκα αν εμφανιζόταν ως συσκευή του συστήματος και υπήρχε δυνατότητα ελέγχου μέσω κάποιου προγράμματος;

Σ” αυτό το εγχείρημα δεν θα βασιστούμε στο Arduino. Η πλατφόρμα δεν θ” αποτελεί τον πρωταγωνιστή της κατασκευής μας, ούτε θα τη δεσμεύσουμε για τον έλεγχο του ανεμιστήρα. Αντίθετα, θα χρησιμοποιήσουμε το Arduino ελάχιστα και μόνο σε ένα στάδιο της κατασκευής. Όλα αυτά, βέβαια, θα τα δούμε αναλυτικά στη συνέχεια. Για την ώρα, μπορούμε ν” αρχίσουμε αμέσως με τη συλλογή του απαραίτητου hardware&#8230;

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2012/07/12/deltahacker010/" title="deltaHacker 010 – The Hack Resort Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker Ιουλίου (τεύχος 010)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και security που δεν κυκλοφορεί στα περίπτερα και απευθύνεται σε όλους, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.