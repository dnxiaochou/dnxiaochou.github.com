---
layout: post
title: "Python Jannet Numbers"
description: ""
category: 
tags: []
---
{% include JB/setup %}
Jannet完成了两个程序，将一个非负十进制整数转化为其二进制和十六进制数。
十进制转为二进制

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

十进制转为十六进制

    #!/usr/bin/env python
    # This program receives a decimal and print its hexadecimal code
    
    # loop forever
    while (True):
        # wait for user input one number
        raw_n = raw_input ("please input a number: " )
    
        # convert the string 'raw_n' to a number
        n = int (raw_n)
    
        # check if n is zero, print '0' and quit the program
        if n == 0 :
          print (0)
          exit ()
    
        # before entering the loop, declare a variable to save the result
        v = ""
        # loop until n equals to 0
        while (n != 0):
            # get remainder
            v1 = n % 16
    
            if (v1 < 10):
                v1 = bytes(v1)
            elif (v1 == 10):
                v1 = "A"
            elif (v1 == 11):
                v1 = "B"
            elif (v1 == 12):
                v1 = "C"
            elif (v1 == 13):
                v1 = "D"
            elif (v1 == 14):
                v1 = "E"
            else :
                v1 = "F" 
    
            # concatenate strings
            v = v1 + v
    
            # finally change n to n/16
            n = n / 16 
    
        # result is save to variable v, just print it.
        print("The hexadecimal code of %s is: %s" % (raw_n, v))
