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
    
    def xj_dec_to_binary (n):
        res = ""
        while (n != 0):
            r = n % 2
            res = bytes (r) + res
            n = n / 2 
        return res
    
    while (True):
        str_n = raw_input ("please input a number: " )
        n = int (str_n)
        if (n == 0) :
            print (0)
            quit ()
    
        result = xj_dec_to_binary (n)
        print("The binary code of %s is: %s" % (str_n, result))


十进制转为十六进制

    #!/usr/bin/env python
    # This program receives a decimal and print its hexadecimal code

    def xj_hex_digit (n) :
        if (n < 10) :
            return bytes (n)
        elif (r == 10):
            return "A"
        elif (r == 11):
            return "B"
        elif (r == 12):
            return "C"
        elif (r == 13):
            return "D"
        elif (r == 14):
            return "E"
        elif (r == 15):
            return "F"
        else :
            return "X"
    
    
    def xj_dec_to_hex (n) :
        res = ""
        while (n != 0):
            r = n % 16
            r = xj_hex_digit (r)
            res = r + res
            n = n / 16 
        return res
    
    while (True):
        str_n = raw_input ("please input a number: " )
        n = int (str_n)
    
        if (n == 0) :
            print (0)
            exit ()
    
        result = xj_dec_to_hex (n)
        print("The hexadecimal code of %s is: %s" % (str_n, result))
        
