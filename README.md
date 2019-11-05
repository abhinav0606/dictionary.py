# dictionary.py
a dictionary which gives us the meanig of every single word we search so like  i have used used the json file and imported a get_close_matches from the difflib and i have created a good interface for this  
 so this code for that is 
 
 
 import json
from difflib import get_close_matches
data=json.load(open("data.json"))
def translate(n):
    n=n.lower()
    if n in data:
        if len(data[n])>1:
            for i in data[n]:
                print(i)
        else:
            print(data[n][0])
    elif n.title() in data:
        if n.title() in data:
            if len(data[n.title()]) > 1:
                for i in data[n]:
                    print(i)
            else:
                print(data[n.title()][0])
    elif n.upper() in data:
        if n.upper() in data:
            if len(data[n.upper()]) > 1:
                for i in data[n.upper()]:
                    print(i)
            else:
                print(data[n.upper()][0])
    elif len(get_close_matches(n,data.keys()))>0:
        h=get_close_matches(n,data.keys())[0]
        print("we have a closest match for the word")
        d=input("enter y or n for moving forward")
        if d=="y":
            if len(data[h])>1:
                for i in data[h]:
                    print(i)
            else:
                print(data[h][0])
        elif d=="n":
            print("sorry this word doesnt exist")
        else:
            print("you are caugth over wrong keys")
    else:
        print("the word doesnt exist in this dictionary")
word=input("enter the word ")
translate(word)
