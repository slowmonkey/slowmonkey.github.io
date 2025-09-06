---
layout: post
title: "Learning MergeSort"
categories: [learning, sorting, algorithms]
tags: [learning, sorting]
excerpt: Noting down MergeSort for everytime I have to remember it
---

# Introduction

Noting down MergeSort for everytime I have to remember it for interviews.

# How Merge Sort works in my words

1. If the length of the array is more than 1 continue
2. Get the middle of the array
3. Split it left and right
4. Repeat steps 1-3 for each left and right array.
5. When the array size is 1 merge the left and right based on size order.

# Code 
<div>Code Repository: <a class="sidebar-nav-item" href="https://github.com/slowmonkey/learning-mergesort" alt="GitHub - Learning MergeSort Repo" target="_blank"><i class="fab fa-github"></i></a></div>

```
namespace Learnings;

public class Learnings
{
    public static void MergeSort(int[] items)
    {
        // Stop processing if the number of items in the array is 1 or less

        if (items.Length <= 1)
        {
            return;
        }

        // Split the array into 2.

        int middleIndex = items.Length / 2;

        int[] left = new int[middleIndex];
        int[] right = new int[items.Length - middleIndex];

        // Syntax: Array.Copy(source_array, source_starting_index, destination_array, destination_array_starting_index, number_of_items_to_copy)

        Array.Copy(items, 0, left, 0, middleIndex);
        Array.Copy(items, middleIndex, right, 0, items.Length - middleIndex);

        // Sort each array

        MergeSort(left);
        MergeSort(right);

        // Merge the sorted halves

        Merge(items, left, right);
    }

    private static void Merge(int[] result, int[] left, int[] right)
    {
        int resultIndex = 0;
        int leftIndex = 0;
        int rightIndex = 0;

        // Loop through the maximum length array number of times.

        while (resultIndex < result.Length)
        {
            if (leftIndex < left.Length && rightIndex < right.Length)
            {
                if (left[leftIndex] < right[rightIndex])
                {
                    result[resultIndex] = left[leftIndex];
                    leftIndex++;
                }
                else
                {
                    result[resultIndex] = right[rightIndex];

                    rightIndex++;
                }
            }
            else
            {
                // Assumes one of the left or right indexs are already merged
                
                if (leftIndex < left.Length)
                {
                    result[resultIndex] = left[leftIndex];
                    leftIndex++;
                }

                if (rightIndex < right.Length)
                {
                    result[resultIndex] = right[rightIndex];
                    rightIndex++;
                }
            }

            resultIndex++;
        }
    }
}
```

# Time Complexity

MergeSort has a stable O(n log n) time complexity regardless of the sorting scenarios.

# Space Complexity

MergeSort needs extra arrays so has O(n) space complexities.