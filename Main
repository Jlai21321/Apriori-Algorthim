from itertools import combinations, chain
from more_itertools import unique_everseen
import sets
import time
import random
import pandas as pd
import numpy as np
file = open("C:\\Users\\Jonathan Lai\\Downloads\\adult.data")


def process(file):
    record = []
    for line in file:
        varialbeline = line.split(",")
        for x in range(0, len(varialbeline)):
            varialbeline[x] = varialbeline[x] + "_" + str(x)
        record.append(varialbeline)
    # for x in range(0, len(record)):
    # print(record[x])
    return record


def findc1(data, minsupport):
    dict = {}
    n = float((len(data) * minsupport))
    #print(n)
    l1 = []

    for line in data:
        for value in line:
            if (dict.get(value, "none") == "none"):

                dict[value] = 1
            else:
                dict[value] = dict[value] + 1

    for val in dict:
        if dict[val] > n:
            l1.append(val)
    print(len(l1))
    return l1



## Implenmentation from textbook
def has_infrequent_subset(c,k,l):
    c1 = list(combinations(c,k-1))
    for i in c1:
        if i not in l:
            return True
        else:
            return False

def findCK(L,k):
    flatten = [item for subtuple in L for item in subtuple]  # flattens all candidates

    uniqueflatten = list(unique_everseen(flatten))  # gets out duplicate candidates

    c2 = list(combinations(uniqueflatten,k))


   # c2= set(c2)
    for c in c2:
        if has_infrequent_subset(c,k,c2):
            c2.remove((c))
        else:
            continue
    print(len(c2))
    return c2



##todo bug
## Implement shroter

def findLk(ck,minsupport,data):
    minn = float(minsupport*len(data))
    L = []
    count = {}
    for item in ck:
        count[item] = 0

    for value in data:
        for c in ck:
            if set(c).issubset(value):
                count[c] = count[c] +1
    for c in ck:
        if float(count[c]) > minn:
            L.append(c)
    #print(len(L))
    return L



   # for item in ck:
        #if()


    return L
def apriori(file,minsupport):
    Data = process(file)

    L = findc1(Data,minsupport)
    k =2

    fitemsets = []
    while(len(L) !=0):
        if( k == 2):
            c2 = list(combinations(L,2))
            for x in c2:
                if has_infrequent_subset(x,1,L):
                    c2.remove(x)
                else:
                    continue
            Ck = c2


        else:
            Ck = findCK(L,k)
           # print(len(Ck))




    ##todo Reassign L1 = LK after Ck is filtered
        L = findLk(Ck,minsupport,Data)

        fitemsets.append(L)
        k= k +1


    return fitemsets


Item = apriori(file,.6)
