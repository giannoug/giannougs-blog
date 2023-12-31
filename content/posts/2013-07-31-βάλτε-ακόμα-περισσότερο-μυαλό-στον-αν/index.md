---
title: 'Βάλτε (ακόμα περισσότερο) μυαλό στον ανεμιστήρα! [μέρος 1]'
date: 2013-07-31T11:01:30+00:00
url: /βάλτε-ακόμα-περισσότερο-μυαλό-στον-αν/
cover:
    image: περισσότερο-μυαλό-στον-αν.jpg
categories:
  - deltaHacker
  - Σοβαρά
tags:
  - attiny
  - avr
  - microcontroller
  - usb fan

---
Περίπου έναν χρόνο πριν αποφασίσαμε να μετατρέψουμε έναν \*απλό\* ανεμιστήρα USB σε μια κανονική συσκευή USB. Μετά από έναν ολόκληρο χειμώνα διαφόρων σκέψεων και ιδεών, αποφασίσαμε να επιστρέψουμε στο θέμα για να διορθώσουμε ορισμένα bugs και να υλοποιήσουμε μερικές νέες ιδέες!

Αυτή τη φορά δεν θα μιλήσουμε για τις τεχνολογίες που ενσωματώνει ο έξυπνος ανεμιστήρας μας, ούτε θα ασχοληθούμε με την εγκατάσταση των απαραίτητων εργαλείων. Ωστόσο, θα εμβαθύνουμε στα χαρακτηριστικά αυτών των εργαλείων και θα χρησιμοποιήσουμε πιο εξειδικευμένες λειτουργίες, τόσο του hardware όσο και του software. Αρχικά θα λύσουμε όλα τα προβλήματα που εμφανίστηκαν μετά από μερικούς μήνες λειτουργίας και θα δούμε πώς μπορούμε να διορθώσουμε ορισμένα σχεδιαστικά λάθη. Στο επόμενο άρθρο, στο deltaHacker 022, θα χτίσουμε το νέο μας πρόγραμμα, βασισμένοι στη βελτιωμένη μορφή του κυκλώματος και στα νέα χαρακτηριστικά που θέλουμε να αποκτήσει ο ανεμιστήρας. Πριν από όλα αυτά, όμως, πρέπει να μελετήσουμε και να ετοιμάσουμε το νέο hardware. Πριν προχωρήσουμε, θα σας προτείναμε να διαβάσετε τα σχετικά άρθρα στα τεύχη 010 και 011, ώστε να θυμηθείτε τι είχαμε κάνει τότε.

# Ενοχλητικά ζουζούνια

Ξεκινάμε από τα bugs που υπήρχαν αλλά δεν εμφανίστηκαν εξαρχής. Το κυριότερο πρόβλημα που είχε η υλοποίησή μας εντοπιζόταν στη συνάρτηση hadUsbReset. Η συνάρτηση αυτή ήταν υπεύθυνη για την \*σωστή\* ρύθμιση του ρολογιού του μικροελεγκτή, μετά από κάθε του εκκίνηση. Η εν λόγω συνάρτηση αποτελούσε δικό μας κατασκεύασμα και στηριζόταν σε παρόμοιες υλοποιήσεις που είχαμε συναντήσει στο Internet, σε παρόμοια πρότζεκτ. Δυστυχώς η υλοποίησή μας αποδείχτηκε προβληματική &#8212; και γι&#8217; αυτό θα την εγκαταλείψουμε! Στη θέση της θα χρησιμοποιήσουμε μια αντίστοιχη συνάρτηση που ενσωματώνει (πλέον) η ίδια η βιβλιοθήκη V-USB.

Το δεύτερο πρόβλημα που εντοπίσαμε σχετίζεται με το διακόπτη της συσκευής. Εμείς τον χρησιμοποιήσαμε για να \*κόβουμε\* την τροφοδοσία του μικροελεγκτή, κάνοντας τον ανεμιστήρα να σταματάει. Μεγάλο λάθος! Ο δίαυλος USB δεν εντοπίζει τις συσκευές ελέγχοντας αν αντλείται ρεύμα. Το hardware του USB μετράει την αντίσταση μεταξύ του ακροδέκτη D+ και του GND κι αν αυτή η αντίσταση έχει τιμή περί τα 2,2KΩ, θεωρείται ότι έχει συνδεθεί κάποια συσκευή. Για τη σωστή λειτουργία του ανεμιστήρα το κύκλωμά μας διέθετε ακριβώς μια τέτοια αντίσταση, στους κατάλληλους ακροδέκτες του διαύλου USB. Επομένως, όταν κλείναμε τον διακόπτη ο μικροελεγκτής και ο ανεμιστήρας σταματούσαν, αλλά ο υπολογιστής συνέχιζε να βλέπει μια συσκευή την οποία ονόμαζε &#8220;Unknown device&#8221;!

Ο κυριότερος λόγος για τον οποίο πέρασε αρκετός καιρός μέχρι να ασχοληθούμε ξανά με τον ανεμιστήρα και το λογισμικό του, ήταν η δύσκολη πρόσβαση στον μικροελεγκτή. Για τη δοκιμή μιας νέας έκδοσης του firmware έπρεπε να ξεκοιλιάσουμε τον ανεμιστήρα κι αυτό σήμαινε βίδες, βιδάκια, στριμωγμένα καλώδια και δεν συμμαζεύεται! Για να αλλάξουμε αυτή την κατάσταση και να διευκολύνουμε τις περαιτέρω επεμβάσεις, αποφασίσαμε να ξεκινήσουμε εγκαθιστώντας στον μικροελεγκτή έναν USB bootloader.

> Διαβάστε ολόκληρο το άρθρο στο <a href="http://deltahacker.gr/2013/06/30/deltahacker021/" title="deltaHacker 021 - Cool Summer Edition" target="_blank" rel="noopener noreferrer nofollow" class="broken_link">deltaHacker 021 (τεύχος Ιουνίου 2013)</a>.
