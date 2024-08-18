---
title: 算法设计的清明作业
date: 2024-04-07 07:56:23
tags: 作业
hidden: true
---
## 题目
![tm](tm.png)

### 1
```Python
def find_max_position(arr):
    max_value = arr[0]
    max_position = 0

    for i in range(1, len(arr)):
        if arr[i] > max_value:
            max_value = arr[i]
            max_position = i

    return max_position

# 示例：使用数组 [3, 5, 8, 6, 9, 1, 7]
arr = [3, 5, 8, 6, 9, 1, 7]

max_position = find_max_position(arr)
print("最大元素的位置是:", max_position)
```

### 3
```Python
def sort_negative_before_positive(arr):
    # Step 1: Count negative elements
    num_negatives = sum(1 for num in arr if num < 0)

    # Step 2: Create a new array with the same length
    result = [None] * len(arr)

    # Step 3: Fill the new array with negative elements first, then positive ones
    neg_index = 0
    pos_index = num_negatives

    for num in arr:
        if num < 0:
            result[neg_index] = num
            neg_index += 1
        else:
            result[pos_index] = num
            pos_index += 1

    return result


# Example usage:
input_arr = [-3, 4, -1, Ⅱ, 6, -2, 0]
sorted_arr = sort_negative_before_positive(input_arr)
print(sorted_arr)
```

### 4
```Python
def max_crossing_sum(arr, start, mid, end):
    left_sum = float('-inf')
    curr_sum = 0
    for i in range(mid, start - 1, -1):  # Traverse from mid-1 to start
        curr_sum += arr[i]
        left_sum = max(left_sum, curr_sum)

    right_sum = float('-inf')
    curr_sum = 0
    for i in range(mid + 1, end + 1):  # Traverse from mid+1 to end
        curr_sum += arr[i]
        right_sum = max(right_sum, curr_sum)

    return left_sum + right_sum  # Return the maximum crossing sum


def max_subarray_sum(arr, start=0, end=None):
    if end is None:
        end = len(arr) - 1

    if start == end:  # Base case: single element
        return arr[start]

    mid = (start + end) // 2
    left_max = max_subarray_sum(arr, start, mid)
    right_max = max_subarray_sum(arr, mid + 1, end)
    cross_max = max_crossing_sum(arr, start, mid, end)

    return max(left_max, right_max, cross_max)


# Example usage:
input_arr = [-2, 1, -3, 4, -1, 2, 1, -5, 4]
max_sum = max_subarray_sum(input_arr)
print(max_sum)
```

### 5
```Python
def find_median_of_merged_arrays(A, B):
    # Step 2: Merge sorted arrays A and B into a list C
    C = []
    i = j = 0
    while i < len(A) and j < len(B):
        if A[i] < B[j]:
            C.append(A[i])
            i += 1
        else:
            C.append(B[j])
            j += 1

    # Step 3: Add remaining elements of the non-exhausted array
    while i < len(A):
        C.append(A[i])
        i += 1
    while j < len(B):
        C.append(B[j])
        j += 1

    # Step 4: Compute the median of merged array C
    length = len(C)
    if length % 2 == 1:  # Odd length
        median = C[length // 2]
    else:  # Even length
        median = (C[length // 2 - 1] + C[length // 2]) / 2

    return median


# Example usage:
A = [1, 3, 5]
B = [2, 4, 6]
median = find_median_of_merged_arrays(A, B)
print("Median of merged arrays:", median)
```

### 后注
在Python中，`//` 和 `/` 这两个运算符都用于执行除法操作，但它们之间存在显著的区别：

**`/` (普通除法)**:
- `a / b` 表示浮点数除法，无论操作数 `a` 和 `b` 是整数还是浮点数，结果总是以浮点数形式返回。
- 结果保留除法运算的小数部分，确保精度，即得到的是最精确的商。
- 示例：`5 / 2` 返回 `2.5`，`7 / 3` 返回 `2.3333333333333335`。

**`//` (地板除法、整数除法)**:
- `a // b` 表示整数除法，也称为地板除或向下取整除法，返回除法结果的整数部分，即不保留小数，且结果始终小于或等于真实的商。
- 如果 `a` 和 `b` 都是整数，结果也将是整数。如果其中一个或两个操作数是浮点数，结果将是浮点数，但仍然是向下取整的整数部分。
- 示例：`5 // 2` 返回 `2`，`7 // 3` 返回 `2`。

总结来说，`/` 用于计算精确的浮点数除法结果，而 `//` 用于计算除法的整数部分，向下取整。在需要得到除法结果的整数值且不需要小数部分时，通常会使用 `//` 运算符。如果需要进行比例计算、得到精确商或进行数学计算需要保留小数部分，则使用 `/` 运算符。