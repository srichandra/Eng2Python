
-------------------------------------------------------------------------------------------------------------------------------------------------------------------

EnglishToPython_Final.ipynb is the main code notebook which has all steps from data cleaning, model training, testing. 

https://drive.google.com/file/d/1DxHGSRonfYqh3lc3nYkjF4IyQvpG0Mux/view?usp=sharing has the final model

Pythoncode_GLOVE notebook is the code notebook for training glove embeddings for python
https://drive.google.com/file/d/1DxHGSRonfYqh3lc3nYkjF4IyQvpG0Mux/view?usp=sharing has the glove model


# Data Cleaning

1. Dataset consists of english sentence as a comment followed by python code corresponding to the sentence. 
2. Read the dataset line by line to extract the pairs of english sentence and corresponding python block. 
3. Difficulty in extraction comes from the fact that the english sentences start from "#" as well all the comments in python. We create an ignore pattern to first filter out lines that contain In[00]: or just #[num] or just bunch of \s or contain word "driver block/code". 
4. Also, we use a minimum length based on the histogram of english sentence to filter out the comments. 


# Model Architecture and Salient features

We have used the same architecture from the Attention is all you need paper and discussed in the class

# Loss function

We have cross entropy loss function

# Data Preparation

1. For english, we have used spacy tokenization module
2. For python code part, we have used tokenize module which parses the python code into string tokens. For characters like '\n', white spaces - we have encoded them with their token names like newline, indent, endline etc

# Data Extension

No external data has been used for model training

# Python Code embedding strategy

1. We have trained 256dim glove embeddings for python. 
2. We used python code from the given training data along with data from codesearch challenge
https://github.com/github/CodeSearchNet#data-details
3. We then trained our own glove model. 



# Evaluation Metrics

We have BLEU metric as evaluation score. We were able to achieve 42.51% BLEU score on validation data

# 25 Examples

## Example 1:

Input: 

4 . write a python function to add two user provided numbers and return the sum

Model Output:
```
def add_two_numbers(num1,num2):
    sum=num1+num2
    return sum

```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111862834-de64d700-897d-11eb-93b0-1e242515a3e4.png)

## Example 2:

Input: 

write a python program that multiplies a tuple n times and print the result

Model Output:
```
my_tuple=(1,2,3,4,5,6,8,10)
n=3
print(my_tuple*n)

```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863013-dfe2cf00-897e-11eb-9b73-c1828dc3ff05.png)

## Example 3:

Input: 

calculate length of a string

Model Output:

```
word="hello world"
print(f"length of string: {len(word)}")


```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863103-64355200-897f-11eb-868d-22bb108edb41.png)

## Example 4:

Input: 

write a python program to print odd numbers in a list

Model Output:

```
list1=[10,21,4,45,66,93,11,70,88,66,93]
odd_nos=list(filter(lambda x:x%2!=0,list1))
print("odd numbers in the list: ",odd_nos)

```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863196-0e14de80-8980-11eb-8a28-4c13f992830f.png)

## Example 5:

Input: 

write a python program to print a list after removing elements from index 1 to 4

Model Output:

```
list1=[11,5,17,18,23,50,50]
del list1[5:5]
print(*list1)

```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863234-461c2180-8980-11eb-82b4-1164d75d5d52.png)

## Example 6:

Input: 

write python program to read the contents of a file in reverse order

Model Output:

```
filepath=<unk>
with open(filepath,'r')as f:
    words=line.read()
    for line in reversed(words):
        print(line)


```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863296-c773b400-8980-11eb-806a-8411cdffd419.png)

## Example 7:

Input: 

write a python program to count how many times each letter occurs in a string

Model Output:

```
word='the quick brown fox jumps over the lazy dog'
countmap={}
for letter in string:
    if letter in countmap:
        countmap[letter]+=1
    else:
        countmap[letter]=1
print(<unk>)

```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863432-8c25b500-8981-11eb-908a-666332388fb8.png)

## Example 8:

Input: 

write a python function to check whether a number is perfect

Model Output:

```
def is_perfect_square(n):
    if n==1:
        return n//2
    else:
        return false
```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863464-c55e2500-8981-11eb-8674-c56befbe8db9.png)

## Example 9:

Input: 

find the sum of the cube of each digit

Model Output:

```
num=int(input("enter a number: "))
sum=0
temp=num
while temp>0:
    digit=temp%10
    sum+=digit**3
    temp//=10
    temp//=10
if num==sum:
    print(num,"is an armstrong number")
else:
    print(num,"is not an armstrong number")
    
```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863520-1c63fa00-8982-11eb-81b7-55757cff4bb4.png)

## Example 10:

Input: 

63 write a python function which returns true if all the numbers in a list negative , else return false

Model Output:

```
def make_all_negative(nums):
    return[num if num<0 else 0 for num in nums]
```
Attention:

![alt text](https://user-images.githubusercontent.com/7562089/111863574-74026580-8982-11eb-853e-dbd5eac6607b.png)

## Example 11:

Input: 

write a python function to find the compound interest in python when principle amount , rate of interest and time is given

Model Output:

```
def compound_interest(p,r,t):
    amount=(p*r*t)/100
    return ci
```
## Example 12:

Input: 

write a program to create a string variable and print the amount of memory it consumes

Model Output:

```
import sys
string_var=<unk>
print(sys.getsizeof(string_var))

```

## Example 13:

Input: 

write a python function to find the power of a number using recursions

Model Output:

```
def power(n,p):
    if(p==1):
        return(n*(n-1))
    else:
        return(power(n-1)

```

## Example 14:

Input: 

 write a function to return the perimeter of a isoscales triangle

Model Output:

```
def cal_perimeter_iso_triangle(s1,s2):
    return 2*s1+s2

```

## Example 15:

Input: 

36 python parse datetime from string

Model Output:

```
from datetime import datetime
datetime_object=datetime.strptime(<unk>,'%b %d %y %i:%m%p')
print(datetime_object)

```

## Example 16:

Input: 

write a python program to print 5 random integers between 10 and 20

Model Output:

```
import random
print random.random()
```

## Example 17:

Input: 

write a python program to print unique numbers in a list

Model Output:

```
numbers=[1,2,3,4,5,6,8,8,4,8,10]
unique=set(numbers)
print(<unk>,unique)
```

## Example 18:

Input: 

write a function that returns cosine value of the input

Model Output:

```
def derivative_cos(x:float)->float:
    import math
    return-(-x)
```
## Example 19:

Input: 

write a function to reverse a string

Model Output:

```
def reverse_string(string):
    return string[::-1]
```
## Example 20:

Input: 

access first characters in a string

Model Output:

```
word="hello world"
letter=word[-1]
print(f"first charecter in string:{letter}")
```
## Example 21:

Input: 

write a python program to multiply three numbers and print the result

Model Output:

```
num1=10
num2=6.3
num3=-2.3
product=num1*num2*num3
print(f'product: {product}')

```
## Example 22:

Input: 

write a program to remove the duplicate words

Model Output:

```
test_string='the king is the one'
unique=set(str1.split())
print(unique)

```

## Example 23:

Input: 

write a program to remove the duplicate words

Model Output:

```
import random
heads=0
tails=0
while(n>0):
    for j in range(0,11):
        if(random.choice():
            heads+=1
        else:
            tails+=1
    print(<unk>)

```

## Example 24:

Input: 

write a function to rotate string left by a given length

Model Output:

```
def rotate(input,d):
    lfirst=input[0:d]
    lsecond=input[0:len(input)-d]
    return(lsecond+lfirst)
```

## Example 25:

Input: 

write a function to multiplies two lists element wise only if numbers are odd

Model Output:

```
def adds_listevenelements(l1:list,l2:list):
    return[i*j for i,j in zip(l1,l2)]
```
