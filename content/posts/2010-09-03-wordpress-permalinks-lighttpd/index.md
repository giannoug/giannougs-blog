---
title: WordPress permalinks στον lighttpd
date: 2010-09-03T16:18:21+00:00
url: /wordpress-permalinks-lighttpd/
cover:
    image: light_logo.png
categories:
  - How-to και άλλα
tags:
  - lighttpd
  - mod_rewrite
  - permalinks
  - pretty urls
  - rewrite
  - rewrite rules
  - wordpress

---
Το WordPress υποστηρίζει &#8220;pretty urls&#8221;. Τι σημαίνει αυτό; Μπορεί να &#8220;αλλάζει&#8221; τα URL και να τα κάνει &#8220;όμορφα&#8221;. Για παράδειγμα, αν δεν υπήρχε αυτή η δυνατότητα το URL αυτού του άρθρου θα ήταν _/?p=1176_. Με pretty url γίνεται _/wordpress-pretty-urls-lighttpd/_.

Σε αυτό βοηθάει ο web server. Το WordPress έχει την δυνατότητα να ρυθμίζει μόνο του τον Apache μέσω του αρχείου _.htaccess_, ένα αρχείο απ&#8217; το οποίο ο Apache διαβάζει κάποιες per directory ρυθμίσεις. Ο lighttpd δεν υποστηρίζει κάτι αντίστοιχο αυτού και επειδή δεν τον χρησιμοποιούν πολλά άτομα δε θα βρείς και πολύ υλικό στο Internet. Για την ακρίβεια θα βρεις, αλλά τα περισσότερα μπλέκονται απίστευτα πολύ. Αρκεί να αναφέρω ότι είχα πετύχει άρθρο με γύρω στις 50 γραμμές rewrite rules (άσ&#8217; το καλύτερα δηλαδή).

Ο lighttpd είναι ευχαριστημένος και με την παρακάτω γραμμή μόνο, αρκεί να την προσθέσεις στο κατάλληλο σημείο του config του, δηλαδή μέσα στο directive του domain του WordPress blog.

{{< highlight conf >}}
server.error-handler-404 = "/index.php"
{{< / highlight >}}

Παράδειγμα:  
{{< highlight conf >}}
$HTTP["host"] =~ "(^|\.)example\.com$" {  
  server.document-root = "/var/www/example.com"  
  server.error-handler-404 = "/index.php"  
}  
{{< / highlight >}}