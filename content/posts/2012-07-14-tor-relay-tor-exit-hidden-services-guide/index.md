---
title: Μπείτε στο κύκλωμα, ενεργά! (Tor, Tor Relay, Tor Exit)
date: 2012-07-14T11:04:02+00:00
url: /tor-relay-tor-exit-hidden-services-guide/
cover:
    image: tor-relay-tor-exit-hidden-services-guide.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - hidden services
  - tor
  - tor exit
  - tor relay

---
Τι θα λέγατε αν σας πρότειναν να αναλάβετε το ρόλο ενός μυστικού πράκτορα, σε μια μυστική αποστολή μεταφοράς ευαίσθητων μηνυμάτων; Ακούγεται συναρπαστικό, έτσι δεν είναι; Θα συμφωνήσουμε, αλλά πρέπει να σας θυμίσουμε ότι κάτι τέτοιο θα ήταν και άκρως επικίνδυνο. Εναλλακτικά, μπορείτε να στήσετε ένα Tor relay node ή ένα Tor exit node και να συνεισφέρετε στο δίκτυο Tor, μεταφέροντας κρυπτογραφημένα μηνύματα, πέρα-δώθε! Κι αν έχετε διάθεση για ακόμα πιο ενεργή ανάμειξη στο «κύκλωμα», μπορείτε να σηκώσετε μια δικτυακή υπηρεσία αποκλειστικά \*εντός\* του Tor network&#8230;

Στο <a href="http://deltahacker.gr/2012/04/06/deltahacker007/" title="deltaHacker 007 – A View to a Hack Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker 007</a> (Απρίλιος 2012) γνωρίσαμε το κρυφό κομμάτι του Internet, το λεγόμενο deep web, μέσα από το δίκτυο Tor. Στο παρόν άρθρο θα εμβαθύνουμε στη λειτουργία αυτού του ευφυέστατα στημένου δικτύου και θα δούμε πώς μπορούμε να συμμετάσχουμε σε αυτό ενεργά! Όπως αναφέραμε και στο προηγούμενο άρθρο, κάθε φορά που συνδεόμαστε στο Tor τα δικτυακά μας πακέτα διέρχονται (κρυπτογραφημένα) από μια τυχαία κατασκευασμένη αλληλουχία από Tor nodes. Στο τέλος αυτής της μυστικής διαδρομής εξέρχονται προς το «απλό» Internet, μέσω κάποιου Tor exit node. Βέβαια, όταν επισκεπτόμαστε κάποια τοποθεσία του deep web, τα πακέτα μας παραμένουν στο δίκτυο Tor και καταλήγουν σε μηχανήματα με τα λεγόμενα hidden services. Αν αυτές οι έννοιες σας ξενίζουν, μην ανησυχείτε καθόλου. Σε λίγο θα τις γνωρίσετε καλά και μάλιστα στην πράξη. Είτε θέλετε να συμμετάσχετε στο Tor ως ένας απλός κόμβος είτε να αποτελέσετε πέρασμα από το Tor προς το απλό Internet είτε να σηκώσετε τη δική σας υπηρεσία στο deep web, θα σας δείξουμε όλα τα απαραίτητα βήματα!

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2012/07/12/deltahacker010/" title="deltaHacker 010 – The Hack Resort Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker Ιουλίου (τεύχος 010)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και security που δεν κυκλοφορεί στα περίπτερα και απευθύνεται σε όλους, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.
