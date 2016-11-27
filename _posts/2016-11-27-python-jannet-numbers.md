---
layout: post
title: "Python Jannet Numbers"
description: ""
category: 
tags: []
---
{% include JB/setup %}
Jannet实现了如何将一个非负十进制整数转化为其二进制和十六进制形式。在实现中，定了了4个函数：
xj_get_binary_char()返回一个二进制字符，对于非法参数，返回一个字符X；
xj_get_hex_char()返回一个十六进制字符，对于非法参数，返回一个字符X；
xj_dec_to_binary()返回一个二进制字符串；
xj_dec_to_hex()返回一个十六进制字符串。
最后，在程序入口，调用Python内置的函数raw_input()接受用户输入，分别调用以上函数转化为二进制字符串和十六进制字符串并打印出来。

    #!/usr/bin/env python
    
    # receives a number and return its binary char
    def xj_get_binary_char (n) :
        if (n >= 0 & n <=1) :
            return bytes (n)
        else :
            return "X"
    
    
    # receives a number and return its hexadecimal char
    def xj_get_hex_char (n) :
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
    
    
    # receives a number and return its binary string
    def xj_dec_to_binary (n):
        res = ""
        while (n != 0):
            r = n % 2
            r = xj_get_binary_char (r)
            res = r + res
            n = n / 2 
        return res

    
    # receives a number and return its hexadecimal string
    def xj_dec_to_hex (n) :
        res = ""
        while (n != 0):
            r = n % 16
            r = xj_get_hex_char (r)
            res = r + res
            n = n / 16 
        return res
    
    
    # program entry
    while (True):
        str_n = raw_input ("please input a number: ")
        n = int (str_n)
        if (n == 0) :
            print (0)
            quit ()
    
        result = xj_dec_to_binary (n)
        print ("The binary code of %s is: %s" % (str_n, result))
    
        result = xj_dec_to_hex (n)
        print ("The hexadecimal code of %s is: %s" % (str_n, result))
    
        print ("")

在Linux系统的终端里，运行上述Python脚本文件，测试结果如下。

    please input a number: 91
    The binary code of 91 is: 1011011
    The hexadecimal code of 91 is: 5B
    
    please input a number: 250
    The binary code of 250 is: 11111010
    The hexadecimal code of 250 is: FA
    
    please input a number: 2147483647
    The binary code of 2147483647 is: 1111111111111111111111111111111
    The hexadecimal code of 2147483647 is: 7FFFFFFF
    
    please input a number: 0
    0

