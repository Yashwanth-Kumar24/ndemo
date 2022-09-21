## Lab 04

- Name: Pranav Rao
- Email: ponugoti.2@wright.edu

## Part 1 Answers

1. `grep -P '\d{3}-\d{3}-\d{4}\s{1}(x|X)\d{4}' grepdata.txt`
2. `grep -E '(CA|ca)' grepdata.txt`
3. `grep -P '^[\w]*\@[a-z]*\.[a-z]*$' grepdata.txt`
4. `grep -P '^[a-zA-Z]{3}\.\s{1}\d{1,2}\,\s{1}2\d{2}[^0]'' grepdata.txt`

## Part 2 Answers
#### The following commands only print the result on the shell
1. `sed 's/<[\/][a-zA-Z0-9]*>//g' sedfile.html`
2. `sed 's/^\s*<li>/- /g' sedfile.html`
3. `sed 's/\s*<h1>/# /g' sedfile.html`
4. `sed 's/\s*<h2>/## /g' sedfile.html`
5. `sed 's/<ul>//' sedfile.html | sed 's/<html>//'`
6. `sed 's/Batches/Matches/g' sedfile.html`
#### In order to create .md file, I have run the 1st command followed by `sed <condition> sedfile.html > sedfile.md`. This resulted in new file sedfile.md
#### In the further commands, I have used `sed -i <condition> sedfile.md`, this resulted me to get final expected output in sedfile.md file

## Part 3 Answers

1. `awk '$1 ~ /^Bil/ {print $1}' records.txt`
2. `awk '$4==42 {print $3}' records.txt`
3. `awk '$3 ~ /@wright.edu$/ {printf "%s, %s: %s\n",$2,$1,$3}' records.txt`
4. `awk '$3 ~ /@wright.edu$/ && $6==1234 {printf "%s favourite number is: %d\n",$2,$4}' records.txt`
5. `awk '$6="N0T@PL@!NP@$$W0RD"' records.txt | tee updaterecords.txt`
