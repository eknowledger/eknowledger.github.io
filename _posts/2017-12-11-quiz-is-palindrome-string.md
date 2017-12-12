---
layout: single
title: "Is a Palindrome String?"
excerpt: "Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases."
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Given a string, determine if it is a palindrome, considering only alphanumeric characters and ignoring cases.


### Example

    Input : "Red rum, sir, is murder" is a palindrome, while"
    Output: true

    Input : "Ahmed is Engineer"
    Output: false

    Input : ""
    Output: true

    Input : "a"
    Output: true

## Analysis

A usual palindrome problem is a little easier, since the assumption is all sort of charachters are included, for instance "abba" is a simple palindrome. we can use two indcies to traverse forward and backward and compare values for matching, an algorithm of time compliexity `O(n/2)`

{% highlight csharp %}
    public static bool IsPalindrome(string str)
    {
        if (string.IsNullOrEmpty(str) || str.Length == 1)
            return true;

        int i = 0; int j = str.Length - 1;
        while(i < j)
        {
            if (str[i++] != str[j--]) return false;
        }


        return true;
    }
{% endhighlight %}

But in this case we want to only consider **alphanumeric characters and ignoring cases** , we still run a forward and backward traverse , for each charachter  we will check is letter is letter or digit using framework helper methdo `Char.IsLetterOrDigit()` , if not then we move get next charachter until we get an alphanumeric char.

## CSharp Solution

{% gist eea4185d5743b0da6e347ae785b47d57 %}

_Happy Coding!_