---
title: 'OpenVZ: AK-47s, for everyone! (μέρος 1, η απαραίτητη υποδομή)'
date: 2012-10-12T11:28:56+00:00
url: /openvz-tutorial-ak-47s-for-everyone-part-1/
cover:
    image: openvz-tutorial-ak-47s-for-everyone-part-1.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - linux
  - openvz
  - server
  - virtual machines

---
Όσο κι αν μας αρέσουν οι δοκιμές και τα πειράματα με διάφορες δικτυακές υπηρεσίες κι όχι μόνο, κανείς δεν θέλει να παίζει με το κύριο σύστημά του. Γι” αυτό και στρεφόμαστε στις εικονικές μηχανές, οι οποίες επιτρέπουν κάθε είδους δοκιμή, χωρίς τον παραμικρό κίνδυνο για το κανονικό σύστημα. Φυσικά, μια εικονική μηχανή μπορεί να λειτουργεί «παράλληλα» με πολλές ακόμα εικονικές μηχανές. Έτσι, μπορούμε να σχηματίζουμε ολόκληρα (εικονικά) δίκτυα και μέσα σε αυτά να πραγματοποιούμε ακόμα πιο σύνθετες δοκιμές και πειράματα. Αν νομίζετε ότι κάτι τέτοιο προϋποθέτει πανάκριβο εξοπλισμό, κάνετε λάθος. Θα σας αποδείξουμε τι εννοούμε.

Δεν θα ήταν ωραία αν μπορούσαμε να τρέχουμε όλα τα virtual machines μας, σε ένα μόνο μηχάνημα; Δεν θα ήταν ακόμα καλύτερα αν είχαμε πρόσβαση σ” όλες τις εικονικές μηχανές, μέσω δικτύου; Προφανώς, θα μου πείτε, αλλά θα σκεφτείτε ότι κάτι τέτοιο αποτελεί ακριβό χόμπι! Ένα μηχάνημα, ικανό να σηκώσει πέντε μ” έξι εικονικές μηχανές, με το VirtualBox ή το VMware, χρειάζεται αρκετά ισχυρό hardware, το οποίο καλό θα ήταν να υποστηρίζει κι όλες τις σχετικές τεχνολογίες (virtualization). Αυτό το τελευταίο σημαίνει ότι το μηχάνημα θα έπρεπε να είναι και σχετικά σύγχρονο. Με άλλα λόγια, το μηχάνημα που επιτρέπει την \*ομαλή\* λειτουργία πολλών εικονικών μηχανών, είναι ακριβό. Μήπως όμως παραβλέπουμε κάτι; Τα VirtualBox και VMware δεν αποτελούν μονόδρομο. Υπάρχει κάποιος άλλος τρόπος να πετύχουμε το σκοπό μας, χωρίς να καταξοδευτούμε. Στη συνέχεια θα εξερευνήσουμε αυτόν τον τρόπο και θα μάθουμε πώς μπορούμε να μετατρέψουμε ένα παλιό netbook ή ένα παροπλισμένο PC, σ” ένα ολοκληρωμένο εργαστήριο/δίκτυο εικονικών μηχανών! Τι λέτε, ξεκινάμε;

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2012/10/11/deltahacker013/" title="deltaHacker 013 (τεύχος Οκτωβρίου 2012)" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker 013 (τεύχος Οκτωβρίου 2012)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking, δίκτυα, ασφάλεια, προγραμματισμό και ηλεκτρονικά που δεν κυκλοφορεί στα περίπτερα και απευθύνεται σε όλους, θα τις <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">βρείτε εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.