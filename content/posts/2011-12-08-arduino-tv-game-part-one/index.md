---
title: TV-Game με το Arduino! (μέρος 1 από 2)
date: 2011-12-08T18:47:15+00:00
url: /arduino-tv-game-part-one/
cover:
    image: arduino-tv-game-part-one.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - arduino
  - arduino tv-game
  - avr
  - tv-game

---
Το Arduino έτσι, το Arduino αλλιώς, το Arduino παρά πέρα… Τον τελευταίο καιρό ακούμε συνεχώς για hacks και για projects που στηρίζονται στο Arduino. Μήπως έφτασε η ώρα να κάνουμε κι εμείς κάτι με αυτό το μαραφέτι;

Προφανώς κι έφτασε, αλλά πριν ξεκινήσουμε θα πρέπει να πάρουμε τα πράγματα από την αρχή. Τι είναι αυτό το Arduino και τι κάνει; Το Arduino δεν είναι τίποτα άλλο παρά ένας μικροελεγκτής AVR από την Atmel, «τυλιγμένος» με το κατάλληλο software ώστε να ‘ναι προσιτός στους χρήστες που δεν είχαν ποτέ σχέση με τα ηλεκτρονικά. Έρχεται με το δικό του περιβάλλον ανάπτυξης (Integrated Development Environment, IDE) αλλά και με τις δικές του βιβλιοθήκες, οι οποίες επιτρέπουν σ’ οποιονδήποτε έχει βασικές προγραμματιστικές γνώσεις να φτιάξει, χμ, οτιδήποτε μπορεί να φανταστεί!

> Διαβάστε όλο το άρθρο στο deltaHacker Νοεμβρίου (τεύχος 002). Τα περιεχόμενα του τεύχους είναι <a href="http://deltahacker.gr/2011/11/02/deltahacker-002-anatoliko-timor-edition/" title="deltaHacker 002 – Ανατολικό Τιμόρ edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και infosec, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">παραδίπλα</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.