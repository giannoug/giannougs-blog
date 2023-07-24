---
title: Linux backup scripts, ασφάλεια με copy paste
date: 2010-06-01T11:37:11+00:00
url: /linux-backup-scripts/
cover:
  image: broken-harddisk.jpg
categories:
  - How-to και άλλα
tags:
  - backup
  - linux
  - script
  - ubuntu

---
Δεν χρειάζεται να κάτσεις να σκεφτείς τρόπους και να χάνεσαι στα documentation και στις man pages. Έκανα εγώ την βρώμικη δουλειά για &#8216;σένα. Δεν έχεις να κάνεις τίποτα άλλο παρά να αντιγράψεις τα παρακάτω script ή μέρη αυτών, να τα πειράξεις κατάλληλα και να απολαύσεις τα backup. Έχω σχολιάσει αρκετά τον κώδικα οπότε δε νομίζω να χρειάζεται παραπάνω εξήγηση. Δεν ξέρω αν υπάρχει άλλος, καλύτερος τρόπος ή αν έκανα κάποιο λάθος στις εντολές. Δουλεύει μια χαρά και δεν υπάρχει λόγος να το πειράξω 🙂  


{{< highlight bash >}}
#!/bin/sh  
# Backup script by giannoug <blog.giannoug.gr>  
# Gets a copy of the databases.  
# Should be executed once per day.  
# * 23 * * * /root/daily-backup.sh  
##

# Save the date  
export d=\`date +"%d-%m-%Y"\`

# Go to /tmp and make a folder  
cd /tmp  
mkdir daily-$d  
cd daily-$d

# Get the SQL backups  
mysqldump -u root -pYourPasswordHere giannougs-blog > giannougs-blog.sql

# Wrap it up in a nice gzip archive  
tar -czf daily-backup_$d.tar.gz *

# Bring it to /root and give read/write  
# permissions ONLY to root (not the best, but&#8230;)  
mv daily-backup_$d.tar.gz /root/daily  
cd /root  
chmod 600 daily/daily-backup_$d.tar.gz

# Delete files older than 7 days  
find daily/* -mtime +7 -exec rm {} \;

# Push the new file to another server  
# Uses scp with key authentication  
scp -i slave-pc-key daily/daily-backup_$d.tar.gz giannoug@slave-pc.giannoug.gr:~/backups

# Delete temp folders  
rm -rf /tmp/daily-$d  
{{< / highlight >}}

{{< highlight bash >}}
#!/bin/sh  
# Backup script by giannoug <blog.giannoug.gr>  
# Gets all the sites and their databases.  
# Should be executed once per week.  
# * * * * 1 /root/weekly-backup.sh  
##

# Save the date  
export d=\`date +"%d-%m-%Y"\`

# First, make sure /var/www is owned by lighttpd  
chown -R www-data:www-data /var/www

# Go to /tmp and make a folder  
cd /tmp  
mkdir weekly-$d  
cd weekly-$d

# Make a tar of /var/www  
cd /var/www  
tar -cf /tmp/weekly-$d/sites.tar *  
cd /tmp/weekly-$d

# Get the SQL backups  
mysqldump -u root -pYourPasswordHere giannougs-blog > giannougs-blog.sql

# Get some configs  
cp /etc/lighttpd/conf-available/50-vhosts.conf .

# Wrap it up in a nice gzip archive  
tar -czf weekly-backup_$d.tar.gz *

# Bring it to /root and give read/write  
# permissions ONLY to root (not the best, but&#8230;)  
mv weekly-backup_$d.tar.gz /root/weekly  
cd /root  
chmod 600 weekly/weekly-backup_$d.tar.gz

# Delete files older than 30 days  
find weekly/* -mtime +30 -exec rm {} \;

# Push the new file to another server  
# Uses scp with key authentication  
scp -i slave-pc-key weekly/weekly-backup_$d.tar.gz giannoug@slave-pc.giannoug.gr:~/backups/weekly

# Delete temp folders  
rm -rf /tmp/weekly-$d  
{{< / highlight >}}

Αυτά!