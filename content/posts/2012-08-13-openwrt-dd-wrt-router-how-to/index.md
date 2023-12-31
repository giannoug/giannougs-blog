---
title: Χαρίστε απίστευτες δυνατότητες στον οικιακό σας router
date: 2012-08-13T09:53:32+00:00
url: /openwrt-dd-wrt-router-how-to/
cover:
    image: openwrt-dd-wrt-router-how-to.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - dd-wrt
  - how to
  - linux
  - openwrt
  - router

---
Πρακτικά, όλοι έχουμε από ένα router στο σπίτι. Η δικτυακή αυτή συσκευή είναι σαν μια γέφυρα μεταξύ των υπολογιστών/δικτυακών συσκευών του σπιτιού και του Internet. Στη συντριπτική πλειονότητά τους, τα routers αυτά συνδέονται σε μια τηλεφωνική πρίζα κι αναλαμβάνουν να μεταφέρουν δεδομένα TCP/IP μέσα από τον τηλεφωνικό χαλκό, από και προς την εταιρεία που μας προσφέρει το Internet. Το πρωτόκολλο που χρησιμοποιούν γι” αυτό το κομμάτι της διαδρομής είναι συνήθως το *DSL.

Παρόλο που έχουμε συνηθίσει να τα λέμε «routers», στην πραγματικότητα πρόκειται για modem/routers. Πράγματι, πέρα από το να αποτελούν γέφυρες ή πύλες μεταξύ των υπολογιστών του τοπικού δικτύου (συνήθως του οικιακού) και κάποιου εξωτερικού δικτύου (συνήθως του Internet), στην πραγματικότητα έχουν και την «εξυπνάδα» ενός modem, π.χ., για να διαμορφώνουν το σήμα ώστε να ταξιδεύει μέσα από το τηλεφωνικό καλώδιο με βάση το πρωτόκολλο *DSL.

Μια αρκετά μεγάλη κοινότητα έχει αναπτυχθεί γύρω από τους routers, με σκοπό να τους κάνει αρκετά καλύτερους. Η κοινότητα αυτή έχει δημιουργήσει δύο διαφορετικές διανομές Linux, ικανές να μετατρέψουν έναν απλό, οικιακό router, σε έναν πλήρη, ικανότατο server. Όπως και με κάθε διανομή (και κοινότητα) Linux, έτσι κι εδώ η καθεμία έχει την δική της φιλοσοφία κι ακολουθεί διαφορετικό δρόμο από τις άλλες. Ονομαστικά, οι δύο αυτές διανομές είναι το dd-wrt και το OpenWRT. Θα μιλήσουμε και για τα δύο, αλλά θα ασχοληθούμε εκτενέστερα με το dd-wrt.

> Διαβάστε όλο το άρθρο στο <a href="http://deltahacker.gr/2012/08/07/deltahacker011/" title="deltaHacker 011 – Lazy August Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker Αυγούστου (τεύχος 011)</a>. Όλες τις πληροφορίες για τις συνδρομές στο deltaHacker, το μοναδικό μηνιαίο περιοδικό με θεματολογία ethical hacking και security που δεν κυκλοφορεί στα περίπτερα και απευθύνεται σε όλους, θα τις βρείτε <a href="http://deltahacker.gr/subscriptions/" title="Πληροφορίες συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">εδώ ακριβώς</a>. Για παραγγελίες μεμονωμένων τευχών ή συνδρομών συμπληρώστε τη <a href="http://deltahacker.gr/order/" title="Αγορές τευχών & συνδρομών" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">σχετική φόρμα</a>.
