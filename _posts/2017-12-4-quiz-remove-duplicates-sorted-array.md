---
layout: single
title: "Remove Duplicates from Sorted Array"
excerpt: "Write an a efficient function to remove duplicate numbers from a sorted array"
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Given a sorted array, remove the duplicates in place such that each element appear only once and return array.

### Example

    Input : [1,1,2,2,3,4,4]
    Output: [1,2,3,4]

    Input : [1,1,1]
    Output: [1]

    Input : [1,2]
    Output: [1,2]
## Analysis

The problem can be solved easily by using an extra temp array and copy the unique elements to the temp array. Or with a little more work to do all work in place, if we have memory constraints.

Either case solution should run in `O(n)` speed.

**Note** Arrays are fixed length data structure, changing the length of an array in place is usually done by copying elements; We will use built in  `Array.Resize()` apis to resize in place, and assume operation runs in `O(1)`. But in reality this is not the case.
{: .notice--warning}

## Solution 1 - Using Temporary Array

This solution will create a temporary auxiliary array to store unique numbers.

The algorithm will traverse the original array, comparing each element with next, if not duplicate, it will copy the unique element to temporary.

**C#**
{% highlight csharp %}
        public static int[] RemoveDuplicates(int[] array)
        {
            if (array.Length < 2)
                return array;

            int[] tempArray = new int[array.Length];

            int j = 0; // unique nubmer index
            for(int i = 0; i < array.Length-1; i++)
                if (array[i] != array[i + 1])
                    tempArray[j++] = array[i]; // tempArray[j] = array[i]; j = j+1;

            // Copy last element in main array duplicate or not
            // since it will not get copied as part of the loop
            tempArray[j++] = array[array.Length -1];

            // There are no better method to resize arrays
            Array.Resize(ref tempArray, j);
            return tempArray;
        }
{% endhighlight %}

Time Complexity  : `O(n)`
Space Complexity : `O(n)`
{: .notice--success}

## Solution 2 - Using Constant Space

This solution will utilize the same array to sort out the duplicates. It will only use an extra index to keep track of the last unique nubmer in the array.

The algorithm will traverse the array forward, comparing element with next element; if not equal elements it will copy the current element to last unique index location. Then array will be reseized at last unique index.

**C#**
{% highlight csharp %}
        public static int[] RemoveDuplicates(int[] array)
        {
            if (array.Length < 2)
                return array;
            // unique number index
            int j = 0;
            for (int i = 0; i < array.Length - 1; i++)
                if (array[i] != array[i + 1])
                    array[j++] = array[i]; // array[j] = array[i]; j = j+1;

            array[j++] = array[array.Length - 1];

            Array.Resize(ref array, j);
            return array;

        }

{% endhighlight %}

Time Complexity  : `O(n)`
Space Complexity : `O(1)`
{: .notice--success}

## Bouns

What if duplicates are allowed at most **twice** ?

### Example

    Input : [1,2,2,2,3,3,3,3,4,5,5,5]
    Output: [1,2,2,3,3,4,5]

The solution still straightforward, we will use a counter for duplicates and check for how many duplicates desired

**C#**
{% highlight csharp %}
        public static int[] RemoveDuplicates5(int[] array)
        {
            if (array.Length < 2)
                return array;
            // unique number index
            int j = 0;
            int k = 0; // count for how many duplicates allowed
            for (int i = 0; i < array.Length - 1; i++)
                if (array[i] != array[i + 1])
                {
                    array[j++] = array[i]; // array[j] = array[i]; j = j+1;
                    k = 0;
                }
                else
                {
                    if (k < 1)
                    {
                        array[j++] = array[i];
                        k = k + 1;
                    }
                }

            array[j++] = array[array.Length - 1];

            Array.Resize(ref array, j);
            return array;
        }

{% endhighlight %}

Time Complexity  : `O(n)`
Space Complexity : `O(1)`
{: .notice--success}

_Happy Coding!_