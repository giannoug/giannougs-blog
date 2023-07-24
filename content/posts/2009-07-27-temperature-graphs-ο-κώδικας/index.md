---
title: Temperature graphs, ο κώδικας
date: 2009-07-27T19:52:16+00:00
url: /temperature-graphs-ο-κώδικας/
categories:
  - Projects
tags:
  - basic stamp
  - bs2
  - room temperature graphs
  - slave-pc

---
Μετά τον θάνατο του σκληρού του Slave-PC, χάθηκαν όλα τα graphs.. Φυσικά ξενέρωσα και το παράτησα 😛 Όπως είχα πει σε ένα σχόλιο στο προηγούμενο άρθρο, θα έδινα τον κώδικα.. Θα δώσω και του μικροεπεξεργαστή, αλλά και του server με την ελπίδα ότι θα βοηθήσουν κάποιον 🙂

Πρώτα του μικροεπεξεργαστή. Ο μικροεπεξεργαστής είναι ο Basic Stamp II της Parallax (τα έχω ξαναπεί άπειρες φορές, αλλά αυτός που θα πέσει σε αυτό το άρθρο πρώτη φορά, δεν θα το ξέρει 😛 ). Η γλώσσα που είναι γραμμένο το πρόγραμμα είναι η PBASIC. Δεν είναι τέλειο, αλλά δουλεύει. Είχα ξεκινήσει πολλά διαφορετικά, αλλά αυτό επέζησε 🙁 Δεν εξηγώ τι κάνει και πως.. Είναι ανώφελο και βαρετό 😛  

{{< highlight basic >}}
' Program: Room Stats  
' Author : giannoug  
' - email: giannoug@gmail.com  
' - site : blog.giannou.net  
' Version: V1.0  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' {$STAMP BS2}  
' {$PBASIC 2.5}  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' Σταθερές / Μεταβλητές  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
'Εντολές DS1620  
Wconfig CON $0C ' Protocol for 'Write Configuration.'  
CPU CON %10 ' Config bit: serial thermometer mode.  
Cont CON %00 ' Config bit: continuous conversions after start.  
StartC CON $EE ' Protocol for 'Start Conversion.'  
StopC CON $22 ' Protocol for 'Stop Conversion.'  
RTemp CON $AA ' Protocol for 'Read Temperature.'  
'&#8212;&#8212;-

DSdata VAR Word ' Word variable to hold 9-bit data  
cmd VAR Word  
i VAR Byte  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' Pins  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
DQ CON 2 ' Pin 2 <=> DQ  
CLK CON 1 ' Pin 1 => CLK  
RST CON 0 ' Pin 0 => RST

GLed CON 3 ' Pin 3 => Green led  
OLed CON 4 ' Pin 4 => Orange Led  
RLed CON 5 ' Pin 5 => Red led  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' Σετάρισμα  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
Setup:  
LOW RST: HIGH CLK  
PAUSE 100  
HIGH RST  
SHIFTOUT DQ,CLK,LSBFIRST,[Wconfig,CPU+Cont]  
LOW RST  
PAUSE 50  
HIGH RST  
SHIFTOUT DQ,CLK,LSBFIRST,[StartC]  
LOW RST

LOW GLed: LOW OLed: LOW RLed

FOR i = 0 TO 3  
PULSOUT GLed, 1000: PULSOUT OLed, 1000: PULSOUT RLed, 1000  
PAUSE 150  
NEXT

PAUSE 1000  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' Κύριο πρόγραμμα  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
DO

GOSUB GetTemp  
GOSUB SendData

PAUSE 1000

LOOP  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
' Υπορουτίνες  
'=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
GetTemp:  
FOR i = 1 TO 4  
PULSOUT OLed, 1000  
PAUSE 100  
NEXT

HIGH RST  
SHIFTOUT DQ,CLK,LSBFIRST,[RTemp]  
SHIFTIN DQ,CLK,LSBPRE,[DSdata\9]  
LOW RST

DSdata = DSdata/2  
RETURN

SendData:  
DEBUG "T", SDEC DSdata  
FOR i = 1 TO 4  
PULSOUT GLed, 1000  
PAUSE 100  
NEXT  
RETURN  
{{< / highlight >}}

Σειρά έχει του server.. Και εδώ είχα ξεκινήσει πολλά, πραγματικά ΠΟΛΛΑ 😛 Δεν είναι καθόλου καλό, είναι γραμμένο στο πόδι, κυριολεκτικά. Την δουλειά του την κάνει όμως! Προσοχή μην την πάθεις όπως εγώ.. Αν το τρέξεις 500 φορές για παράδειγμα, και δεν έχεις πάνω τον μικροεπεξεργαστή, και τα 500 θα μείνουν ανοιχτά περιμένοντας να πάρουν δεδομένα απ' τη σειριακή! Θέλει προσοχή ή μια IF να ελέγχει 🙂

{{< highlight python >}}
#!/usr/bin/env python  
# Program: Room Stats  
# Author : giannoug  
# - email: giannoug@gmail.com  
# - site : blog.giannou.net  
# Version: V1.0  
#=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-=====-  
import serial, sys, time

if 1 == 2:  
sys.stdout.write("0")  
exit()

ser1al = serial.Serial(0)  
time.sleep(1)

data = ser1al.read(4)  
temp = data.replace("T", "")

sys.stdout.write(temp)  
ser1al.close()

exit()  
{{< / highlight >}}

Σκέφτομαι να το ξαναξεκινήσω, αλλά αυτή τη φορά να μην βασίζεται σε κάποιον υπολογιστή.. Ιδανικό θα είναι να χρησιμοποιήσω ένα Arduino με μια Ethernet Shield και μια κάρτα SD για να κρατάει τα δεδομένα.. Δυστυχώς αυτό θα στοιχήσει και δεν είναι καιρός για έξοδα τώρα!!