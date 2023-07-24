---
title: 'C# snippet για έλεγχο νέων email στο GMail'
date: 2010-09-01T09:55:46+00:00
url: /check-for-new-mails-gmail-c-sharp/
cover:
    image: dot_net_logo.png
categories:
  - Μαλακίες
tags:
  - .net
  - arduino
  - 'c#'
  - csharp
  - gmail
  - snippet
  - visual studio

---
Καθαρίζοντας ξεχασμένα project στον σκληρό έπεσα πάνω σε ένα project που δεν θυμάμαι τι έκανε&#8230; Με λίγες ματιές στον κώδικα θυμήθηκα ότι ήταν ένα πρόγραμμα το οποίο έλεγχε αν έχεις νέα email και άναβε ένα led στο Arduino. Για κάποιο λόγο δε δούλευε σωστά και με τις μέρες το παράτησα και το ξέχασα. Σήμερα είναι και η μέρα του για delete 😛 Το μόνο που αξίζει να κρατηθεί είναι η μέθοδος για τον έλεγχο νέων email που είχα φτιάξει.

Είχα φάει όλο το Internet για να βρω πως γίνεται τότε. Τελικά βαρέθηκα και αποφάσισα να φτιάξω μια δική μου. Το αποτέλεσμα το βλέπεις παρακάτω. Το username και το password είναι hardcoded αλλά δεν είναι δύσκολο να μπουν ως παράμετροι. Δεν ξέρω αν υπάρχει άλλος, γρηγορότερος τρόπος με κάποιο άλλο parser, αλλά αυτό κάνει την δουλειά 😛 Ακόμη, θα μπορούσε να είναι πιο μαζεμένη αλλά αυτό δεν μας νοιάζει αυτή την στιγμή.

{{< highlight csharp >}}
private bool newMailExist()  
{  
XmlUrlResolver resolver = new XmlUrlResolver();  
resolver.Credentials = new NetworkCredential("USERNAME", "PASSWORD");

XmlReaderSettings settings = new XmlReaderSettings();  
settings.XmlResolver = resolver;

XmlReader reader = XmlReader.Create("https://mail.google.com/mail/feed/atom", settings);

reader.ReadToFollowing("fullcount");  
int sth = reader.ReadElementContentAsInt();

return sth >= 1;  
}  
{{< / highlight >}}