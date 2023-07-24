---
title: Amiga Guru Meditation, με την αγάπη του jQuery
date: 2010-07-14T16:26:49+00:00
url: /amiga-guru-meditation-jquery-implementation/
cover:
  image: Amiga-Guru-Meditation-Error.jpg
categories:
  - Projects
tags:
  - amiga
  - guru meditation
  - html
  - jquery

---
Πριν 1 ή 1.5 χρόνο ήθελα να αλλάξω την κλασική default σελίδα του lighttpd σε κάτι πιο ωραίο αλλά και έξυπνο. Δεν θυμάμαι πως, αλλά μου ήρθε η ιδέα να την κάνω ίδια με το [Guru Meditation](http://en.wikipedia.org/wiki/Guru_Meditation) της [Amiga 500](http://en.wikipedia.org/wiki/Amiga_500). Έτσι και έκανα. Χτες, για κάποιο λόγο μου βίδωσε να την αλλάξω.

Για αρχή έφτιαξα την HTML μιας και για να κάνω center την εικόνα είχα φτιάξει div που το κέντραρα με 50% και άλλες τέτοιες μαλακίες. Δεν πειράζει αν δεν κατάλαβες, ούτε εγώ κατάλαβα τι είχα κάνει, για αυτό και το προσπερνάμε. Δούλευε πάντως. Αφού λοιπόν την έστρωσα λίγο καλύτερα, καθώς διάβαζα το meditation του Guru, πρόσεξα που λέει &#8220;Press left mouse button to continue&#8221;. Μηχανικά το έκανα. Προφανώς δεν έγινε τίποτα στην οθόνη, αλλά στο κεφάλι μου έβρεχε ιδέες. Αποφάσισα να το κάνω όπως το βίντεο παρακάτω. Δεν δείχνει ακριβώς αυτό που θέλω να πετύχω, αλλά you get the idea!

Όταν πατούσες το αριστερό mouse button, έκανε reset. Πως μπορούσε να γίνει αυτό σε σελίδα; Φυσικά με jQuery, απλά και γρήγορα. Αφού έψαξα λίγο γρήγορα βρήκα τις μεθόδους που με ενδιέφεραν. Για αρχή χρειάζεται η _[.css](http://api.jquery.com/css/)_, για να μπορείς να αλλάζεις το property του _background-color_. Ακόμη, χρειάζεται κάποια για παύση, εδώ έρχεται η _[.delay](http://api.jquery.com/delay/)_. Οι δύο τους μαζί δεν δουλεύουν γιατί η _.css_ δεν μπαίνει στο queue για τα effect. Διαβάζοντας τα σχόλια στην σελίδα της _.delay_ έπεσα πάνω στο παρακάτω.

{{< highlight js >}}
$("body").css({"background-color": "#FF0000"})  
.delay(1000).queue(function () {$(this).css({"background-color": "#ABC"});$(this).dequeue();})  
.delay(1000).queue(function () {$(this).css({"background-color": "#FFFFFF"});$(this).dequeue();})  
{{< / highlight >}}

Αυτό ήταν ότι χρειαζόμουν. Με λίγο tweaking δούλεψε! Επίσης χρειάστηκαν αρκετές άλλες που θα βρεις μελετώντας. Παρακάτω υπάρχει το _.zip_ με όλα τα αρχεία. Μπορείς να το ξεκοιλιάσεις, να το αναβαθμίσεις και να το κάνεις καλύτερο. Ένα demo μπορείς να βρεις εδώ: <a href="http://giannou.net/" class="broken_link" rel="nofollow">giannou.net</a>.

<p class="changelog">
  Δεύτερη έκδοση πάνω, η πρώτη είχε ένα λαθάκι&#8230;
</p>

<p class="download">
  [download id=&#8221;3&#8243;]
</p>

<p class="download">
  <del datetime="2010-07-14T18:19:05+00:00">[download id=&#8221;2&#8243;]</del>
</p>
