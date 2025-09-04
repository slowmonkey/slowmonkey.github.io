---
layout: post
title: "Learning QuickSort"
categories: [learning, sorting, algorithms]
tags: [learning, sorting]
excerpt: Noting down QuickSort for everytime I have to remember it
---

# Introduction

Noting down QuickSort for everytime I have to remember it for interviews.

# How QuickSort works in my words

1. Pick a value as the starting point
2. Move the lower values to the left and the higher values to the right. 
3. The algorithm will put the pivot value in the correct spot.
4. Now you have 2 smaller piles. Note that the piles are not necessarily sorted.
5. With each pile repeat the steps above.

# Code 
<div>Code Repository: <a class="sidebar-nav-item" href="https://github.com/slowmonkey/learning-quicksort" alt="GitHub - Learning QuickSort Repo" target="_blank"><i class="fab fa-github"></i></a></div>

```
namespace Learnings;

public class Learnings
{
    public static void QuickSort(int[] items, int leftIndex, int rightIndex)
    {
        // Only continue sorting if the index pointers have not crossed.

        if (leftIndex < rightIndex)
        {
            // Get the index of the pivot value we are using.

            int pivotIndex = Partition(items, leftIndex, rightIndex);

            // Sort the left side

            QuickSort(items, leftIndex, pivotIndex - 1);

            // Sort the right side

            QuickSort(items, pivotIndex + 1, rightIndex);
        }
    }

    public static int Partition(int[] items, int leftIndex, int rightIndex)
    {
        // Take the right most value of the set of items we are sorting as the pivot value.

        int pivot = items[rightIndex];

        // Set the left boundary to be the left index - 1.

        int index = leftIndex - 1;

        // Loop through from the left index to the right index - 1

        for (int counter = leftIndex; counter <= rightIndex - 1; counter++)
        {
            // If the item is less than the pivot value swap them around and increment the left boundary. 
            // IE. Move to the next value to swap against.
            if (items[counter] < pivot)
            {
                index++;
                Swap(items, index, counter);
            }
        }

        // Swap the existing left index value with the right most index value.

        Swap(items, index + 1, rightIndex);

        // Return the current location of the left index + 1
        return index + 1;
    }

    public static void Swap(int[] items, int leftIndex, int rightIndex)
    {
        int temp = items[leftIndex];
        items[leftIndex] = items[rightIndex];
        items[rightIndex] = temp;

        Console.WriteLine("Now: " + string.Join(", ", items));
    }
}
```

# Time Complexity

The average time of using a QuickSort is O(n log n).  
But in it's worse secnario it is O(n^2).

A worse case scenario for QuickSort is when the pivot value used splits the array into 1 element on one side and the rest on the other. Or when the array is already sorted in ascending or descending order.

To avoid this you can mitigate it by doing some of the following:
- User different stragegy of selecting the pivot value. eg. Randomly or using a median of some sort.
- Change to a different sort if the recursion depth traversed is too deep.