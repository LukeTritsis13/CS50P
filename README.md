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




