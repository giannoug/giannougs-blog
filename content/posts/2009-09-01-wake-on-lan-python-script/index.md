---
title: Wake On Lan Python script
date: 2009-09-01T14:18:00+00:00
url: /wake-on-lan-python-script/
categories:
  - How-to και άλλα
tags:
  - home server
  - linux
  - python
  - wol

---
Τον τελευταίο καιρό, που έχει πέσει η μεγάλη βαρεμάρα, σαν καλός geek είπα να ξεκαθαρίσω τα αρχεία του PCιού μου.. Κακώς το ξεκίνησα βέβαια, αλλά μια ψυχή που είναι να βγεί ας βγεί 😛 Κλασικά, βρήκα άπειρα ξεχασμένα αρχεία από εποχές προιστορικές όπως [αυτό εδώ](http://thepiratebay.org/torrent/5072846) το torrent.. 😛 Δε ξέρω γιατί δε λέει seeders και leechers, πάντως είναι αρκετοί!

Κάτι άλλο που βρήκα πριν λίγο.. Ένα script που είχα για να ξεκινάω το PC μέσω του home server! Πάρα πολύ βολικό.. 😉  


{{< highlight python >}}
[code language=&#8221;python&#8221;]  
\# wol.py  
#  
\# Copyright (C) 2002 by Micro Systems Marc Balmer  
\# Written by Marc Balmer, marc at msys.ch, http://www.msys.ch/  
\# This code is free software under the GPL licence  
import struct, socket

def WakeOnLan(ethernet_address):  
addr\_byte = ethernet\_address.split(&#8216;:&#8217;)  
hw\_addr = struct.pack(&#8216;BBBBBB&#8217;, int(addr\_byte[0], 16),  
int(addr_byte[1], 16),  
int(addr_byte[2], 16),  
int(addr_byte[3], 16),  
int(addr_byte[4], 16),  
int(addr_byte[5], 16))

msg = &#8216;\xff&#8217; \* 6 + hw_addr \* 16

s = socket.socket(socket.AF\_INET, socket.SOCK\_DGRAM)  
s.setsockopt(socket.SOL\_SOCKET, socket.SO\_BROADCAST, 1)  
s.sendto(msg, (&#8216;<broadcast>&#8217;, 9))  
s.close()

WakeOnLan(&#8216;FF:FF:FF:FF:FF:FF&#8217;)  
exit()  
{{< / highlight >}}

Μη ξεχάσεις ότι **πρέπει να ενεργοποίησεις το WoL** απ&#8217; το BIOS του υπολογιστή που θες να ανοίγεις τρέχοντας το script και **να βάλεις την MAC address του**.

Καλό remote power on! 😉