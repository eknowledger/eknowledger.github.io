---
layout: single
title: "Search Insert Position"
excerpt: "Write a function to find index of element in an array or return, and if not found return index where it should be inserted in order."
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Given a sorted array and a value, return the index if the target is found. If not, return the index where it would be if it were inserted in order. You may assume no duplicates in the array.

### Example

    Input : [1,3,5,6] , value = 5
    Output: 2

    Input : [1,3,5,6] , value = 2
    Output: 1

    Input : [1,3,5,6] , value = 7
    Output: 4

    Input : [1,3,5,6] , value = 0
    Output: 0

## Analysis

An easy method to solve the problem is to iterate through the array comparing target with value if found return, if greater return index since this will be the location of insertion. ** Time Complexity: `O(n)` **

But we can do better! The problem is a search problem, and as we know `BinarySearch` is better algorithm for searching it will give us ** Time Complexity = `O(log(n))` **

## Solution 1 - Using Recursion

{% highlight csharp %}
    public static int SearchInsert(int[] array, int value)
    {
        var median = array.Length / 2;

        if (array == null || array.Length == 0) return 0;

        return BinarySearch(array, 0, array.Length - 1, value);

    }

    private static int BinarySearch(int[] array, int min, int max, int value)
    {
        var mid = (min + max) / 2;

        if (value == array[mid])
            return mid;

        if (value < array[mid])
            return (min<mid)? BinarySearch(array, min, mid-1, value) : min;
        else
            return (max>mid)? BinarySearch(array, mid+1, max, value) : max+1;
    }
{% endhighlight %}

## Solution 2 - Using a loop

{% highlight csharp %}
    public static int SearchInsert(int[] array, int value)
    {
        if (array == null || array.Length == 0) return 0;

        int i = 0;
        int j = array.Length - 1;

        while(i <= j)
        {
            var mid = (i + j) / 2;

            if (value < array[mid])
                j = mid - 1;
            else if (value > array[mid])
                i = mid + 1;
            else return mid;
        }

        return i;
    }
{% endhighlight %}

Time Complexity  : `O(log(n))`
Space Complexity : `O(1)`
{: .notice--success}

_Happy Coding!_