---
layout: post
title: "Python Jannet Numbers"
description: ""
category: 
tags: []
---
{% include JB/setup %}


#!/usr/bin/env python
# convert decimal to binary

# function: receives a non-negative decimal integer and return its binary 
def xj_dec_to_binary (n):
    res = ""
    while (n != 0):
        r = n % 2
        res = bytes(r) + res
        n = n / 2 
    return res

# loop forever until receives '0'
while (True):
    # wait for user input one number
    str_n = raw_input ("please input a number: " )

    # convert the string 'raw_n' to a number
    n = int (str_n)

    # check if n is zero, print '0' and quit the program
    if n == 0 :
        print (0)
        quit ()

    result = xj_dec_to_binary (n)
    print("The binary code of %s is: %s" % (str_n, result))
