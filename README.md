# PasswordCracking

**Create a simple wordlist**
- `vim pwlist.txt`
- `January
February
March
April
May
June
July
August
September
October
November
December
Password
P@ssw0rd
Forest
htb
Secret
Autumn
Fall
Spring
Winter
Summer`
- Add some years on the password list
- `for i in $(cat pwlist.txt); do echo $i; echo ${i}2019; echo ${i}2020; done > pwlistYear.txt`
- Toggle the password list with hashcat
- `hashcat --force --stdout pwlistYear.txt -r /usr/share/hashcat/rules/best64.rule > pwlisttoggle1.txt`
- Add ! on the password list
- `for i in $(cat pwlisttoggle1.txt); do echo $i; echo ${i}\!; done > pwlistYearEx.txt`
- Toggle the password list again
- `hashcat --force --stdout pwlistYearEx.txt -r /usr/share/hashcat/rules/best64.rule > pwlisttoggle2.txt`
- Toggle various uppercase
- `hashcat --force --stdout pwlisttoggle2.txt -r /usr/share/hashcat/rules/best64.rule -r /usr/share/hashcat/rules/toggles1.rule > pwlisttoggle3.txt`
- Remove the repetative words
- `cat pwlisttoggle3.txt | sort -u > pwlistYearExUnique.txt`
- Remove the words whose length is less than 7
- `cat pwlistYearExUnique.txt | awk 'length($0) > 7'`
