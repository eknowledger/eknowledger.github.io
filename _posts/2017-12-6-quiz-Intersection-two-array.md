---
layout: single
title: "Intersection of Two Arrays"
excerpt: "Write a function to find intersection of two arrays"
tags: [interview,algorithm, data structure]
share: true
comments: true
---

## Problem

Given two arrays, write a function to compute intersection of arrays

### Example

    Input : array1 = [7, 1, 5, 2, 3, 6] , array2 = [3, 8, 6, 20, 7]
    Output: [3,6]

## Find Intersection of Unsorted arrays using Hash

Assuming that arrays doesn't have duplicates, and arrays are not sorted, we can design a solution use an efficient data structure `HashSet` to compute the intersection, the benefit of using `HashSet` add and find operation has `O(1)` time complexity.

* Initialize empty `HashSet`
* Iterate first array and put elements in set
* Iterate second array, and for each element search element in set, if present then its part of intersection.

### Solution - CSharp

{% highlight csharp %}
    public static int[] Intesect(int[] a, int[] b)
    {
        HashSet<int> map = new HashSet<int>();
        List<int> result = new List<int>();

        for (int i = 0; i < a.Length; i++) // o(n)
            map.Add(a[i]); // o(1)

        for (int i = 0; i < b.Length; i++) //o(m)
            if (!map.Contains(b[i])) // o(1)
                result.Add(b[i]);

        return result.ToArray();
    }
{% endhighlight %}

Time Complexity  : `O(m+n)`
Space Complexity : `O(n)`
{: .notice--success}

**Note** I omitted `List<int>` data strucuture size used to capture results from Space Complexity, as well as `.ToArray()` method call used to convert list ot array, from Time Complexity to simplify, in reality these function are not a constant operations.
{: .notice--warning}

## Find Intersection of sorted arrays

If we assume arrays are sorted and doesn't contain duplicates, this will simplify things a bit and give us a chance to optimize the algorithm further.  We can use BinarySearch to compary arrays.

* Iterate through two array
* Compary element in first array with element from second array 
* If less advance first array pointer, if greater advance second array pointer, otherwise its an intersection element

### Solution - CSharp

{% highlight csharp %}
    public static int[] Intesect(int[] a, int[] b)
    {
        int i = 0;
        int j = 0;
        List<int> result = new List<int>();

        while(i < a.Length && j < b.Length)
        {
            if(a[i] < b[j])
                i++;
            else if (a[i] > b[j])
                j++;
            else
            {
                result.Add(a[i]);
                i++;
                j++;
            }
        }

        return result.ToArray();
    }
{% endhighlight %}

Time Complexity  : `O(nlong(n))`
Space Complexity : `O(1)`
{: .notice--success}

_Happy Coding!_