---
title: 00xx const
description: 
permalink: posts/{{ title | slug }}/index.html
date: '2020-06-17'
tags: [cp]
---

I want to compare five things: `char ** a;` `const char ** b;` `char * const * c;` `const char * const * d; const char * const * const e;`

Haha, what are these things? Explained with 5 small programs. Skip to the end of the post for a better explanation.

```c
#include<iostream>
#include <cstring>

void test1(){
    char**s; //s is a pointer to an array;
    s =NULL;
    s =new char*[4];
    for (inti = 0; i <4; ++i){
        s[i] =new char[10];
        strcpy(s[i], "test");
    }
    for (int i = 0; i <4; ++i){
        printf("%s\n", s[i]);
    }
    for (int i = 0; i <4; ++i){
        delete[] s[i];
    }
    delete[] s;
}

void test2(){
    const char**s; //s is a pointer to a string constant
    s =NULL;
    charb[4][10] = {"a","b","c","d"};
    s =new const char*[4];
    for (inti = 0; i <4; ++i){
        s[i] = b[i]; // OK
        //s[i][0] ='d'; //this sentence will report an error, because s[ i] points to a string constant
                    // even if the b[i] string is not a constant (attribute added during compilation)
    }
    for (int i = 0; i <4; ++i){
        printf("%s\n", s[i]);
    }
    delete[] s;
}

void test3(){
    char * const* s; //s points to a constant array, each element of the array is a character pointer constant.
                //the elements of the array cannot be modified, but the string pointed to by the array element can be modified    
    s =NULL;// s is not a constant
    char a[4][10] = {"aa", "bb", "cc", "dd"};
    char * const(b[4]) = {a[0], a[1], a[2], a[3]};
    s = b;
    for (inti = 0; i <4; ++i){
        s[i][1] ='d'; //ok?
        //s[i] =NULL; //report an error because s[i] is a constant
        printf("%s\n", s[i]);
    }
}

void test4(){
    const char * const* s; //s points to an
    array of constant pointers //each element of the array is a character pointer constant, which points to a string constant (tongue twister, this is...)
    s =NULL;// s is not a constant
    char a[4][10] = {"aa", "bb", "cc", "dd"};
    char * const(b[4]) = {a[0], a[1], a[2], a[3]};
    s = b;
    for (inti = 0; i <4; ++i){
        //s[i][1] ='d'; //report an error because s[i][j] is a constant
        //s[i] =NULL; //report an error because s[i] is a constant
        printf("%s\n", s[i]);
    }
}

void test5(){
    char a[4][10] = {"aa", "bb", "cc", "dd"};
    const char * const(b[4]) = {a[0], a[1], a[2], a[3]};
    const char * const * consts = b;
    //s is a constant pointer, pointing to an
    array of constant pointers //Each element of the array is a character pointer constant, pointing to a string constant (this is tongue twister!)
    //s =NULL; //Error, s is a constant
    for (inti = 0; i <4; ++i){
        //s[i][1] ='d'; //report an error because s[i][j] is a constant
        //s[i] =NULL; //report an error because s[i] is a constant
        printf("%s\n", s[i]);
    }
}

intmain(){
    test5();
    return0;
}
```

There is actually a very simple way to read: read the definition from right to left, the result is - `char** s;` `s` is a `pointer 1`, which points to a `pointer 2`, which points to a `pointer 2char`

```c
const char** s;
s is a pointer 1, which points to a pointer 2, which points tochar,charIs a constant

char * const* s;
s is a pointer 1, pointing to a constant 1, constant 1 is a pointer 2, pointer 2 points tochar

const char * const* s;
s is a pointer 1, pointing to a constant 1, constant 1 is a pointer 2, pointer 2 points tochar,charIs a constant

const char * const * consts;
s is a constant 1, constant 1 is a pointer 1, pointer 1 points to a constant 2, constant 2 is a pointer 2, and pointer 2 points tochar,charIs a constant
```
