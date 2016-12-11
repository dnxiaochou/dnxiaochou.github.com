---
layout: post
title: "Python Jannet Numbers"
description: ""
category: 
tags: []
---
{% include JB/setup %}

## 教学

实现非负十进制整数转化为其二进制和十六进制形式。
    
函数xj_get_binary_char()返回一个二进制字符，对于非法参数，返回一个字符X。

    # receives a number and return its binary char
    def xj_get_binary_char (n) :
        if (n >= 0 & n <=1) :
            return bytes (n)
        else :
            return "X"
    
函数xj_get_hex_char()返回一个十六进制字符，对于非法参数，返回一个字符X。

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
    
    
函数xj_dec_to_binary()返回一个二进制字符串。

    # receives a number and return its binary string
    def xj_dec_to_binary (n):
        res = ""
        while (n != 0):
            r = n % 2
            r = xj_get_binary_char (r)
            res = r + res
            n = n / 2 
        return res

    
函数xj_dec_to_hex()返回一个十六进制字符串。

    # receives a number and return its hexadecimal string
    def xj_dec_to_hex (n) :
        res = ""
        while (n != 0):
            r = n % 16
            r = xj_get_hex_char (r)
            res = r + res
            n = n / 16 
        return res
    
    
在程序入口处，调用Python内置的函数raw_input()接受用户输入，分别调用上述已定义的函数将十进制整数转化为二进制字符串和十六进制字符串、并打印出来。

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

## 任务

添加两个函数，实现十进制数转为八进制数。提示：八进制数的字符用0、1、2、3、4、5、6、7表示。

Jannet添加了函数get_octal_char()，其功能是将一个0～7的数字转为字符串；如果输入的是0～7范围之外的数字，返回一个字符X。

    def xj_get_octal_char (n):
        if (n >= 0 & n <= 7):
            return bytes (n)
        else :
            return "X"

Jannet抽象了出来函数dec_to_radix()，形式参数n是输入的十进制数，该函数的功能是把n转为radix进制。

    def xj_dec_to_radix (n, radix) :
        res = ""
        while (n != 0) :
            r = n % radix
            if (radix == 2) :
                r = xj_get_binary_char (r)
            elif (radix == 8) :
                r = xj_get_octal_char (r)
            elif (radix == 16) :
                r = xj_get_hexadecimal_char (r)
            else :
                r = "X"
            res = r + res
            n = n / radix
        return res

在程序入口处，接受输入并转为整数类型后，连续3次调用函数dec_to_radix()，依次使用2、8和16表示要转为的进制。

    while (True):
        str_n = raw_input ("please input a number: ")
        n = int (str_n)
        if (n == 0):
            print (0)
            quit ()
    
        # result = xj_dec_to_binary (n)
        res = xj_dec_to_radix (n, 2)
        print ("The binary of %s is %s" % (str_n, res))
    
        res = xj_dec_to_radix (n, 8)
        print ("The octal of %s is %s" % (str_n, res))
        
        # result = xj_dec_to_hex (n)
        res = xj_dec_to_radix (n, 16)
        print ("The hexadecimal of %s is %s" % (str_n, res))
    
        print ("")

在Linux系统的终端里，运行上述Python脚本文件，测试结果如下。

    please input a number: 250
    The binary of 250 is 11111010
    The octal of 250 is 372
    The hexadecimal of 250 is FA
    
    please input a number: 91
    The binary of 91 is 1011011
    The octal of 91 is 133
    The hexadecimal of 91 is 5B
    
    please input a number: 2147483647
    The binary of 2147483647 is 1111111111111111111111111111111
    The octal of 2147483647 is 17777777777
    The hexadecimal of 2147483647 is 7FFFFFFF
    
    please input a number: 0
    0

## 关于进制转换

以下是十进制、二进制、十六进制和八进制对照表。

    十进制数    二进制数  十六进制数   八进制数
       0        0000       0         0
       1        0001       1         1
       2        0010       2         2
       3        0011       3         3
       4        0100       4         4
       5        0101       5         5
       6        0110       6         6
       7        0111       7         7
       8        1000       8         10
       9        1001       9         11
       10       1010       A         12
       11       1011       B         13
       12       1100       C         14
       13       1101       D         15
       14       1110       E         16
       15       1111       F         17

迄今已经实现了十进制转为二进制、八进制和十六进制。二进制、八进制和十六进制转为十进制相对更为简单。有空时不妨也写出来，权当练习一下Python的语法。

## Jannet的家庭作业

提示1：可以使用Python内置函数

	len()

来返回一个字符串的长度，例如

	len("Hello, world")

得到的结果是

	12

提示2：可以使用Python的字符串分离表达式

	[]

来返回字符串的某一部分。示例：

	str = "Hello, world"
	str[0]                  # 返回H
	str[2]                  # 返回l
	str[11]                 # 返回d
	str[1:4]                # 返回ello

。

Jannet第一次写出的程序长这样 :(

    #!/usr/bin/env python
    while (True):
        str_n = raw_input ("please input a number: ")
        if (str_n == "0"):
            quit ()
        p = len (str_n)
        n = p
        res = 0
        while (n != 0):
            r = str_n[n-1]
            R = int (r)
            m = 1
            i = 1
            while ( i<= p-n ):
                m = 2*m
                i = i+1
            res = R*m + res
            n = n-1
        print ( "The decimal code of %s is : %d" % (str_n , res ))

指导Jannet修改程序，方便以后使用。

    #!/usr/bin/env python
    
    def xj_math_pow (m, n):
        result = 1
        i = 0
        while (i < n):
            result = m * result
            i = i + 1
        return result
    
    
    def xj_binary_to_decimal (str_n):
        length = len (str_n)
        result = 0
        i = 0
        while (i < length):
            tmp = str_n[length - 1 - i]
            bit = int (tmp)
            if (bit == 1):
                result = result + xj_math_pow(2, i)
            i = i + 1
        return result
    
    
    while (True):
        str_n = raw_input ("please input a number: ")
        if (str_n == "0"):
            quit ()
        res = xj_binary_to_decimal (str_n)
        print ("The decimal code of %s is : %d" % (str_n, res))


提示3: Python的字符串比较函数

	cmp()

可以使用cmp来比较两个字符串的大小，若字符串相等，则返回0；否则，如第一个字符串较小，返回负数，否则返回一个正数。示例：

	cmp("abc","abc")          # 返回0
	cmp("abc","abd")          # 返回-1
	cmp("abc","a")            # 返回1

也可以使用>、<、==、>=和<=等操作符来判断。下面是Jannet写的代码。

    #!/usr/bin/env python
    def xj_math_pow(m,n):
        result = 1
        i = 0
        while (i < n):
            result = m * result
            i = i + 1
        return result
    
    def xj_hex_char_to_decimal (n):
        res = ord (n)
        if ((res >= 48) & (res <= 57)):
            res = 0 + (res - 48)
        elif ((res >= 65) & (res <= 70)):
            res = 10 + (res - 65)
        else :
            res = 0
        return res
    
    def xj_hex_char_to_dec (n):
        if ( n == 'A'):
            bit = 10 
        elif (n == 'B'):
            bit = 11
        elif (n == 'C'):
            bit = 12
        elif (n == 'D'):
            bit = 13
        elif (n == 'E'):
            bit = 14
        elif (n == 'F'):
            bit = 15
        elif ((n >= '0') & (n <= '9')):
            bit = int (n)
        else :
            bit = 0
        return bit
    
    def xj_change_to_decimal (m,str_n):
        length = len (str_n)
        result = 0
        i = 0
        while ( i < length ):
            tmp = str_n[length - 1 - i]
            bit = xj_hex_char_to_decimal (tmp)
    #        bit = xj_hex_char_to_dec (tmp)
            if (bit != 0):
                result = result + bit * xj_math_pow(m,i)
            i = i + 1
        return result
    
    while (True):
        str_m = raw_input ("please input the number of the jinzhishu: ")
        m = int(str_m)
        str_n = raw_input("please input a number: ")
        if (str_n == "0"):
            quit()
        res = xj_change_to_decimal (m,str_n)
        print ("The decimal code of %s is : %d" % (str_n,res))


    在Linux终端运行程序，其结果为：
    please input the number of the jinzhishu: 16   
    please input a number: 7FFFFFFF
    The decimal code of 7FFFFFFF is : 2147483647
    please input the number of the jinzhishu: 16
    please input a number: 123456789ABCDEF
    The decimal code of 123456789ABCDEF is : 81985529216486895
    please input the number of the jinzhishu: 16
    please input a number: F 
    The decimal code of F is : 15
    please input the number of the jinzhishu: 8
    please input a number: 123
    The decimal code of 123 is : 83
    please input the number of the jinzhishu: 8
    please input a number: 100
    The decimal code of 100 is : 64
    please input the number of the jinzhishu: 2
    please input a number: 11111110
    The decimal code of 11111110 is : 254
    please input the number of the jinzhishu: 2
    please input a number: 11
    The decimal code of 11 is : 3
