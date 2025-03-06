# HarvardX CS50P's Introduction to Programming with Python

This repo contains the solutions to the problems sets.

- Week 0: Functions, Variables
- Week 1: Conditionals
- Week 2: Loops
- Week 3: Exceptions
- Week 4: Libraries
- Week 5: Unit Tests
- Week 6: File I/O

### Week 0: Functions, Variables

Link to Problem Set 0: https://cs50.harvard.edu/python/2022/psets/0/

**Indoor Voice**
```python
text=input('')

print(text.lower())
```

**Playback Speed**
```python
text=input('')

print(text.replace(' ','...'))
```

**Making Faces**
```python
def main():
    x=input('')
    y=convert(x)
    print(y)

def convert(text):
    a=text.replace(":)","🙂").replace(":(","🙁")
    return a
main()
```

**Einstein**
```python
x=int(input(''))
print(x*(300000000)**2)
```

**Tip Calculator**
```python
def main():
    dollars = dollars_to_float(input("How much was the meal? "))
    percent = percent_to_float(input("What percentage would you like to tip? "))
    tip = dollars * percent
    print(f"Leave ${tip:.2f}")


def dollars_to_float(d):
    y=float(d.lstrip("$"))
    return y


def percent_to_float(p):
    x=float(p.rstrip("%"))/100
    return x

main()
```
### Week 1: Conditionals

Link to Problem Set 1: https://cs50.harvard.edu/python/2022/psets/1/

**Deep Thought**
```python
answer=input("What is the Answer to the Great Question of Life,the Universe,and Everything? ")
answer=answer.lower().lstrip().rstrip()
match answer:
    case "42" | "forty-two" | "forty two":
        print("Yes")
    case _:
        print("No")
```

**Home Federal Savings Bank**
```python
txt = input("Greeting: ")

x = txt.lower().lstrip().rstrip()

if x.startswith("hello"):
	print("$0")
elif x.startswith("h"):
	print("$20")
else:
	print("$100")
```

**File Extensions**
```python
file=input("File name: ")
file=file.lower().lstrip().rstrip()
suffix_l=file.split(".")
suffix=suffix_l[-1]
if suffix=="jpg":
	suffix="jpeg"

if suffix=="jpeg" or suffix=="png" or suffix=="gif":
	print("image/"+suffix)

elif suffix=="zip" or suffix=="pdf":
	print("application/"+suffix)

elif suffix=="txt":
	print("text/plain")

else:
	print("application/octet-stream")
```

**Math Interpreter**
```python
expr=input("Expression: ")
A=expr.split()
x=int(A[0])
z=int(A[-1])
y=A[1]

if y=="+":
	number=x+z

elif y=="*":
	number=x*z

elif y=="-":
	number=x-z

elif y=="/":
	number=x/z

else:
	print("Error")


print("{:.1f}".format(number))
```

**Meal Time**
```python
def main():
    time=input("What time is it? ")
    a=convert(time)
    if 7<=a<=8:
        print("breakfast time")
    elif 12<=a<=13:
        print("lunch time")
    elif 18<=a<=19:
        print("dinner time")


def convert(time):
    hours,minutes=time.split(":")
    hours=float(hours)
    minutes=float(minutes)/60
    return hours+minutes

main()
```
### Week 2: Loops

Link to Problem Set 2: https://cs50.harvard.edu/python/2022/psets/2/

**camelCase**
```python
text=input("Camelcase: ")
new_text=""
for letter in text:
    if letter.isupper():
        letter="_"+letter.lower()
    new_text+=letter
print("Snakecase:",new_text)
```

**CokeMachine**
```python
coins_needed=50
while coins_needed>0:
    print("Amount Due:",coins_needed)
    give_coin=int(input('Insert coin:'))
    if give_coin in [5,10,25]:
        coins_needed-=give_coin
print("Change Owed:",abs(coins_needed))
```
**Just setting up my twttr**
```python
text=input("Input: ")
new_text=""
for letter in text:
    if letter.lower() in ["a","i","e","o","u"]:
        letter=""
    new_text+=letter
print("Output: ",new_text)
```

**Vanity Plates**
```python
def main():

    plate=input("Plate: ")
    if is_valid(plate):
        print("Valid")
    else:
        print("Invalid")



def is_valid(s):
    if s[0:2].isalpha() and s.isalnum() and (2<=len(s)<=6):
        for char in s:
            if char.isdigit():
                index=s.index(char)
                if s[index:].isdigit() and not s[index:].startswith("0"):
                    return True
                else:
                    return False
        return True
main()
```

**Nutrition Facts**
```python
def main():
    item=input("Item:").title()
    if get_calories(item) is not None:
        print("Calories:",get_calories(item))

def get_calories(fruit_given):

#Turning the fruit poster into a dictionary
    fruits=list(("Apple","Avocado","Banana","Cantaloupe","Grapefruit","Grapes",
            "Honeydew Melon","Kiwifruit","Lemon","Lime","Nectarine","Orange",
            "Peach","Pear","Pineapple","Plums","Strawberries","Sweet Cherries","Tangerines"))
    calories=list((130,50,110,50,60,90,50,90,15,20,60,80,60,100,50,70,50,100,50,80))
    fruits_poster=[]
    for i in range(len(fruits)):
        fruits_poster.append(dict(Fruit=fruits[i],Calories=calories[i]))

#Returning the calories of the given fruit
    for i in range(len(fruits_poster)):
        if fruits_poster[i].get("Fruit")==fruit_given:
            return fruits_poster[i].get("Calories")

main()
```


### Week 3: Exceptions

Link to Problem Set 3: https://cs50.harvard.edu/python/2022/psets/3/

**Fuel Gauge**
```python
def main():
    def get_numerator_denominator(Fraction_str):
         numerator, denominator=map(int,Fraction_str.split("/"))
         return numerator, denominator

    while True :
        try:
            F=input("Fraction: ")
            X, Y=get_numerator_denominator(F)
            if X<=Y:
                break
        except (ValueError,ZeroDivisionError) as e:
            pass

    percentage_of_fuel=(X/Y)*100
    if percentage_of_fuel>=99:
        print("F")
    elif percentage_of_fuel<=1:
        print("E")
    else:
        print(str(round(percentage_of_fuel))+"%")
main()
```

**Felipe's Taqueria**
```python
def main():

    Menu={
    "Baja Taco": 4.25,
    "Burrito": 7.50,
    "Bowl": 8.50,
    "Nachos": 11.00,
    "Quesadilla": 8.50,
    "Super Burrito": 8.50,
    "Super Quesadilla": 9.50,
    "Taco": 3.00,
    "Tortilla Salad": 8.00
}

    total=0
    while True :
        try:
            Item=input("Item: ").title()
            if Item in Menu:
                total+=Menu[Item]
                print(f"Total: ${total:.2f}")
        except EOFError:
            print()
            break


    print(f"Total: ${total:.2f}")
main()
```

**Grocery List**
```python
def main():
    grocery_list={}
    while True:
        try:
            item=input().upper()
            if item in grocery_list:
                grocery_list.update({item:grocery_list[item]+1})
            else:
                grocery_list.update({item:1})

        except EOFError:
            print()
            break
    sorted_g_list=sorted(grocery_list.items())
    for i in range(len(sorted_g_list)):
        print(sorted_g_list[i][1],sorted_g_list[i][0])


main()
```

**Outdated**
```python
def main():

    Months=[
    "January",
    "February",
    "March",
    "April",
    "May",
    "June",
    "July",
    "August",
    "September",
    "October",
    "November",
    "December"
]


    while True:
        try:
            Date=input("Date: ").strip()
            if "," in Date:
                Date=Date.replace(","," ")
                Month,Day,Year=Date.split()
                Month=Months.index(Month)+1
                Day=int(Day)
            else:
                Month,Day,Year=Date.split("/")
                Month=int(Month)
                Day=int(Day)

            if 1<=Month<=12 and 1<=Day<=31:
                break
        except ValueError:
            pass
    print(f"{Year}-{Month:02}-{Day:02}")
main()
```

### Week 4: Libraries

Link to Problem Set 4: https://cs50.harvard.edu/python/2022/psets/4/

**Emojize**
```python
import emoji

def main():
    Text=input("Input: ")
    print("Output:",emoji.emojize(Text,language='alias'))
main()
```

**Frank,Ian and Glen's Letters**
```python
import sys
import random
from pyfiglet import Figlet
def main():

    figlet=Figlet()
    
    if len(sys.argv)==1:
        s=input("Input: ")
        figlet.setFont(font=random.choice(figlet.getFonts()))
        print("Output:\n"+figlet.renderText(s))
    elif len(sys.argv)==3 and sys.argv[2] in figlet.getFonts() and sys.argv[1] in ['-f','--font']:
        s=input("Input: ")
        figlet.setFont(font=sys.argv[2])
        print("Output:\n"+figlet.renderText(s))
    else:
        sys.exit("Invalid usage")
main()
```

**Adieu,Adieu**
```python
import inflect
def main():
    p=inflect.engine()
    Names=[]
    while True:
        try:
            name=input("Name: ")
            Names.append(name)
        except EOFError:
            break
    print("Adieu, adieu, to "+p.join(Names))
main()
```
**Guessing Game**
```python
import random
import sys
def main():
    while True:
        try:
            Level=int(input("Level: "))
            random_number=random.randint(1,Level)
            break
        except ValueError:
            pass

    while True:
        try:
            Guess=int(input("Guess: "))
            if Guess>random_number:
                print("Too large!")
            elif Guess<random_number:
                print("Too small!")
            else:
                sys.exit("Just right!")
                
        except ValueError:
            pass

main()
```

**Little Professor**
```python
import random
def main():
    i=1
    l=get_level()
    correct=0
    while i<=10:
        X=generate_integer(l)
        Y=generate_integer(l)
        k=1
        while k<=4:
            if k==4:
                print(f"{X} + {Y} = {X+Y}")
                i+=1
                break
            try:
                Answer=int(input(f"{X} + {Y} = "))
                if Answer==X+Y:
                    correct+=1
                    i+=1
                    break
                else:
                    print("EEE")
                    k+=1
            except ValueError:
                print("EEE")
                k+=1
    print("Score:",correct)

def get_level():
    level=input("Level: ")
    while level not in ("1","2","3"):
        level=input("Level: ")
    return int(level)

def generate_integer(Level):
    if Level==1:
        return random.randint(0,9)
    elif Level==2:
        return random.randint(10,99)
    elif Level==3:
        return random.randint(100,999)
    else:
        raise ValueError

main()
```

**Bitcoin Price Index**
```python
import sys
import requests

try:
    btc=requests.get("https://api.coincap.io/v2/assets/bitcoin").json()
    btc_price=float(btc["data"]["priceUsd"])
    if len(sys.argv)==1:
        sys.exit("Missing command-line argument")
    elif not sys.argv[1].replace(".","").isdigit():
        sys.exit("Command-line argument is not a number")
    print(f"${btc_price*float(sys.argv[1]):,.4f}")
except  requests.RequestException:
    pass
```

### Week 5: Unit Tests

Link to Problem Set 5: https://cs50.harvard.edu/python/2022/psets/5/

**Testing my twttr**
```python
from twttr import shorten

def test_shorten():
    assert shorten("Twitter")=="Twttr"
    assert shorten("ABCDEFG")=="BCDFG"
    assert shorten("AEUIO")==""
    assert shorten("A46e.b")=="46.b"
```

**Back to the Bank**
```python
from bank import value

def test_zero_value():
    assert value("Hello")==0
    assert value("Hello, precious")==0
    assert value("HELLO44")==0

def test_value_20():
    assert value("How's it going?")==20
    assert value("howdy")==20
    assert value("h4393")==20

def test_value_100():
    assert value("Whats happening?")==100
    assert value("lrfrkfkrk")==100
    assert value("1001")==100
```

**Re-requesting a Vanity Plate**
```python
from plates import is_valid

def test_start():
    assert is_valid("AA55")==True
    assert is_valid("2AABCD")==False
    assert is_valid("A244")==False

def test_non_alphanumeric():
    assert is_valid("....4")==False
    assert is_valid(".EEE.,")==False
    assert is_valid(" 224,5A")==False
    assert is_valid("AACD.3")==False

def test_over_6_char():
    assert is_valid("ABD3345")==False
    assert is_valid("AVDC55  ")==False

def test_number_in_middle():
    assert is_valid("AA22AA")==False
    assert is_valid("AA0444")==False

def test_valid_plates():
    assert is_valid("ABCDEF")==True
    assert is_valid("XNZ332")==True
    assert is_valid("AA2204")==True
    assert is_valid("ACDC")==True
```

**Refueling**




### Week 6: File I/O

Link to Problem Set 6: https://cs50.harvard.edu/python/2022/psets/6/

**Lines of Code**
```python
import sys

if len(sys.argv)==1:
    sys.exit('Too few command-line arguments')
elif len(sys.argv)>2:
    sys.exit('Too many command-line arguments')
elif '.py' not in sys.argv[1]:
    sys.exit('Not a python file')

try:
    with open(sys.argv[1],'r') as file:
        lines_of_code=0
        for line in file:
            if not line.lstrip().startswith('#') and len(line.lstrip().rstrip()) >0:
                lines_of_code+=1
    print(lines_of_code)
except FileNotFoundError:
    sys.exit('File does not exist')
```

**Pizza Py**
```python
import sys
import csv
from tabulate import tabulate

if len(sys.argv)==1:
    sys.exit('Too few command-line arguments')
elif len(sys.argv)>2:
    sys.exit('Too many command-line arguments')
elif '.csv' not in sys.argv[1]:
    sys.exit('Not a csv file')

try:
    with open(sys.argv[1]) as file:
        List_of_rows=[]
        reader=csv.reader(file)
        for row in reader:
            List_of_rows.append(row)
    print(tabulate(List_of_rows,headers='firstrow',tablefmt='grid'))
except FileNotFoundError:
    sys.exit('File does not exist')
```

**Scourgify**
```python
import csv
import sys

if len(sys.argv)<3:
    sys.exit('Too few command-line arguments')
elif len(sys.argv)>3:
    sys.exit('Too many command-line arguments')
elif '.csv' not in sys.argv[1] or '.csv' not in sys.argv[2]:
    sys.exit('Not a csv file')

try:
    with open(sys.argv[2],'w',newline='') as newfile:
        writer=csv.DictWriter(newfile,fieldnames=['first','last','house'])
        writer.writeheader()
        with open(sys.argv[1],'r') as file:
            reader=csv.DictReader(file)
            for row in reader:
                last,first=row['name'].split(',')
                house=row['house']
                writer.writerow({'first':first.lstrip(),'last':last,'house':house})
except FileNotFoundError:
    sys.exit(f'Could not read {sys.argv[1]}')
```









