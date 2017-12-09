---
layout: single
title: "Search For Range"
excerpt: "Write a function to find index of element in an array, and if not found return index where it should be inserted in order."
tags: [interview,algorithm, data structure, binary search]
share: true
comments: true
---

## Problem

Given a sorted array of integers, find the starting and ending position of a given target value. Your algorithm’s runtime complexity must be in the order of `O(log n)` . If the target is not found in the array, return `[-1, -1]` .

### Example

    Input : [0,1,3,3,3,3,3,3,3,3,10] , value = 3
    Output: [2,9]

    Input : [5,7,7,8,8,10] , value = 8
    Output: [3,4]

    Input : [] , value = 7
    Output: [-1,-1]

    Input : [1,3,5,6] , value = 5
    Output: [2,2]

## Analysis

The problem forces us to think in `BinarySearch` algorithm's term, since the time complexity myst be in order of `O(log n)` . We can design an algorithm using Binary search to get to the first occurance of element, if found we can traverse teh array backward and forward to find the start and end of the range which will add another `O(m+k)`

<img src="/files/Search_for_Range.png">

## CSharp Solution

{% highlight csharp %}
    public static int[] SearchRange(int[] array, int target)
    {
        if (array == null || array.Length == 0)
            return new[] { -1, -1};

        int min = 0; int max = array.Length - 1;
        return BinarySearchRange(array, min, max, target);
    }

    private static int[] BinarySearchRange(int[] array, int min, int max, int value)
    {
        if (min > max)
            return new[] { -1, -1 };

        if (value == array[min] && value == array[max])
            return new[] { min, max };

        var mid = (min + max) / 2;
        int leftIndex = -1;
        int rightIndex = -1;

        if (value < array[mid])
            return BinarySearchRange(array, min, mid-1, value);
        else if (value > array[mid])
            return BinarySearchRange(array, mid+1, max, value);
        else
        {
            leftIndex = mid;
            rightIndex = mid;

            //traverse backward lookin up for first occurance of value
            var i = mid;
            while (i > min && array[i] ==  value)
                leftIndex = i--; // move backward

            //traverse forward lookin up for last occurance of value
            var j = mid;
            while (j < max && array[j] == value)
                rightIndex = j++; // move forward
        }

        return new[] { leftIndex, rightIndex };
    }
{% endhighlight %}

{% gist 5eaa9523a9df4c225f67f3558c3c64b4 %}

_Happy Coding!_