---
layout: single
title: "Remove Element from Array"
excerpt: "Write a function to remove all instance of a value from an array"
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Given an array and a value, remove all instances of that value in place and return the new arary.

### Example

    Input : [1,10,5,3,4,5,2,5,7,3,7,5] , value = 5
    Output: [1,10,3,4,2,7,3,7]

    Input : [2] , Value =2
    Output: []

    Input : [1,2]  , value = 4
    Output: [1,2]

## Analysis

The problem can be solved easily by using two indices, one pointing at current element, another to point at location to copy elements.
The solution will traverse the array, matching with element value, if matched it will skip ahead, if not matched it will copy to `j` location and increament the location counter.

**Note** Arrays are fixed length data structure, changing the length of an array in place is usually done by copying elements; We will use built in  `Array.Resize()` apis to resize in place, and assume operation runs in `O(1)`. But in reality this is not the case.
{: .notice--warning}


## Solution - CSharp

{% highlight csharp %}
        public static int[] RemoveElement(int[] array, int e)
        {
            int j = 0;
            for (int i = 0; i < array.Length; i++)
                if (array[i] != e)
                    array[j++] = array[i];

            Array.Resize(ref array, j);
            return array;
        }
{% endhighlight %}

Time Complexity  : `O(n)`
Space Complexity : `O(1)`
{: .notice--success}

## Bouns

Given an array of numbers, write a function to move all 0's to the end of it, while maintaining the relative order of non-zero elements.

### Example

    Input : [0,1,0,3,10] 
    Output: [1,3,10,0,0]

### Solution

We can use the same method as before, where we maintain two index, `j` pointing at copy location where we will move elements. and `i` to traverse the array. We traverse the array forward coparing each element with 0 if not equal we copy element to `j` and zero out its location `i`.

### Solution - CSharp

{% highlight csharp %}
    public static int[] MoveZeros(int[] array)
    {
        int j = 0;
        for (int i = 0; i < array.Length; i++)
        {
            if(array[i] != 0)
            {
                var temp = array[i];
                array[i] = 0;
                array[j++] = temp;
            }
        }

        return array;
    }
{% endhighlight %}

Time Complexity  : `O(n)`
Space Complexity : `O(1)`
{: .notice--success}



_Happy Coding!_