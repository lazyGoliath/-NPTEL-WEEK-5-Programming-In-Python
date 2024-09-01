# Week 4 Programming Assignment

- Write three Python functions as specified below. Paste the text for all three functions together into the submission window. Your function will be called automatically with various inputs and should return values as specified. Do not write commands to read any input or print any output.
- You may define additional auxiliary functions as needed.
- In all cases you may assume that the value passed to the function is of the expected type, so your function does not have to check for malformed inputs.
- For each function, there are normally some public test cases and some (hidden) private test cases.
- "Compile and run" will evaluate your submission against the public test cases.
- "Submit" will evaluate your submission against the hidden private test cases. There are 10 private test cases, with equal weightage. You will get feedback about which private test cases pass or fail, though you cannot see the actual test cases.
- Ignore warnings about "Presentation errors".


## The library at the Hogwarts School of Witchcraft and Wizardry has computerized its book issuing process. The relevant information is provided as text from standard input in three parts: information about books, information about borrowers and information about checkouts. Each part has a specific line format, described below.

- ### Information about books

Line format: ```Accession Number~Title`

- ### Information about borrowers

Line format: ```Username~Full Name`

- ### Information about checkouts

Line format: ```Username~Accession Number~Due Date`

Note: Due Date is in YYYY-MM-DD format.

## You may assume that the data is internally consistent. For every checkout, there is a corresponding username and accession number in the input data, and no book is simultaneously checked out by two people.

## Each section of the input starts with a line containing a single keyword. The first section begins with a line containing ```Books```. The second section begins with a line containing  ```Borrowers```. The third section begins with a line containing ```Checkouts```. The end of the input is marked by a line containing ```EndOfInput```.

## Write a Python program to read the data as described above and print out details about books that have been checked out. Each line should describe to one currently issued book in the following format:

```Due Date~Full Name~Accession Number~Title```

## Your output should be sorted in increasing order of due date. For books due on the same date, sort in increasing order of full name.

## Here is a sample input and its corresponding output.

## Sample Input

```bash 
Books
APM-001~Advanced Potion-Making
GWG-001~Gadding With Ghouls
APM-002~Advanced Potion-Making
DMT-001~Defensive Magical Theory
DMT-003~Defensive Magical Theory
GWG-002~Gadding With Ghouls
DMT-002~Defensive Magical Theory
Borrowers
SLY2301~Hannah Abbott
SLY2302~Euan Abercrombie
SLY2303~Stewart Ackerley
SLY2304~Bertram Aubrey
SLY2305~Avery
SLY2306~Malcolm Baddock
SLY2307~Marcus Belby
SLY2308~Katie Bell
SLY2309~Sirius Orion Black
Checkouts
SLY2304~DMT-002~2019-03-27
SLY2301~GWG-001~2019-03-27
SLY2308~APM-002~2019-03-14
SLY2303~DMT-001~2019-04-03
SLY2301~GWG-002~2019-04-03
EndOfInput
```

## Sample Outut

```bash
2019-03-14~Katie Bell~APM-002~Advanced Potion-Making
2019-03-27~Bertram Aubrey~DMT-002~Defensive Magical Theory
2019-03-27~Hannah Abbott~GWG-001~Gadding With Ghouls
2019-04-03~Hannah Abbott~GWG-002~Gadding With Ghouls
2019-04-03~Stewart Ackerley~DMT-001~Defensive Magical Theory
```

### Solution :

```python
# Dictionary to map accession number to title

books = {}

# Dictionary to map username to fullname

borrowers = {}

# List to store checkout data: accumulate, sort and print

checkouts = []

# Find the start of Books data

nextline = input().strip()

while nextline.find("Books") < 0:

    nextline = input().strip()

# Read upto start of Borrowers data

# Skip the line with "Books"

nextline = input().strip()

while nextline.find("Borrowers") < 0:

    (accession_number,title) = nextline.split('~')

    books[accession_number] = title

    nextline = input().strip()

# Read upto Checkout data

# Skip the line with "Borrowers"

nextline = input().strip()

while nextline.find("Checkouts") < 0:

    (username,fullname) = nextline.split('~')

    borrowers[username] = fullname

    nextline = input().strip()

# Process Checkouts

# Skip the line with "Checkouts"

nextline = input().strip()

while nextline.find("EndOfInput") < 0:

    (username,accession_number,due_date) = nextline.split('~')

    checkoutline = due_date+"~"+borrowers[username]+"~"+accession_number+"~"+books[accession_number]

    checkouts.append(checkoutline)

    nextline = input().strip()

# Print the output from checkouts

for checkoutline in sorted(checkouts):

    print(checkoutline)
```

## Sample solutions (Provided by instructor)


```python
 Dictionary to map accession number to title
books = {}
# Dictionary to map username to fullname
borrowers = {}
# List to store checkout data: accumulate, sort and print
checkouts = [] 

# Find the start of Books data
nextline = input().strip()
while nextline.find("Books") < 0:
    nextline = input().strip()

# Read upto start of Borrowers data
# Skip the line with "Books"
nextline = input().strip()
while nextline.find("Borrowers") < 0:
    (accession_number,title) = nextline.split('~')
    books[accession_number] = title
    nextline = input().strip()

# Read upto Checkout data
# Skip the line with "Borrowers"
nextline = input().strip()
while nextline.find("Checkouts") < 0:
    (username,fullname) = nextline.split('~')
    borrowers[username] = fullname
    nextline = input().strip()

# Process Checkouts
# Skip the line with "Checkouts"
nextline = input().strip()
while nextline.find("EndOfInput") < 0:
    (username,accession_number,due_date) = nextline.split('~')
    checkoutline = due_date+"~"+borrowers[username]+"~"+accession_number+"~"+books[accession_number]
    checkouts.append(checkoutline)
    nextline = input().strip()

# Print the output from checkouts
for checkoutline in sorted(checkouts):
    print(checkoutline)
```

The due date for submitting this assignment has passed.
6 out of 6 tests passed.
You scored 100.0/100.