# Fix My Code Challenge

## Description

This project is a collection of programming challenges where existing code contains intentional bugs that need to be identified and fixed. The challenges span multiple programming languages (Python, JavaScript, Ruby, and C) and test understanding of language-specific issues, algorithms, and data structures.

## Project Structure

The project contains 5 tasks, each with a specific bug to fix:

- **Task 0**: FizzBuzz (Python)
- **Task 1**: Print Square (JavaScript)
- **Task 2**: Sort (Ruby)
- **Task 3**: User Password Validation (Python)
- **Task 4**: Doubly Linked List Deletion (C)

## Tasks and Bugs Fixed

### Task 0: FizzBuzz (Python)

**File**: `0-fizzbuzz.py`

**Bug**: Unreachable condition - The check for numbers divisible by both 3 and 5 came after the check for divisibility by 3 only, making it impossible to reach.

**Issue**: Numbers like 15, 30, and 45 printed "Fizz" instead of "FizzBuzz".

**Fix**: Reordered the if-elif conditions to check the most specific condition (divisible by both 3 AND 5) first, before checking individual divisibility.

**Usage**:
```bash
python3 0-fizzbuzz.py <number>
```

**Example**:
```bash
python3 0-fizzbuzz.py 50
# Output: 1 2 Fizz 4 Buzz Fizz 7 8 Fizz Buzz 11 Fizz 13 14 FizzBuzz ...
```

### Task 1: Print Square (JavaScript)

**File**: `1-print_square.js`

**Bug**: The `parseInt()` function used radix 16 (hexadecimal) instead of radix 10 (decimal).

**Issue**: Input "10" was parsed as hexadecimal 0x10 = 16, resulting in a 16x16 square instead of 10x10.

**Fix**: Changed the radix parameter from 16 to 10 in `parseInt(process.argv[2], 10)`.

**Usage**:
```bash
node 1-print_square.js <size>
```

**Example**:
```bash
node 1-print_square.js 5
# Output: 5x5 square of # characters
```

### Task 2: Sort (Ruby)

**File**: `2-sort.rb`

**Bugs**:
1. Inverted comparison operator (`<` instead of `>`) for ascending sort
2. Wrong insertion index (`i - 1` instead of `i`)

**Issue**: Array elements were sorted incorrectly due to backwards comparison logic.

**Fix**:
- Changed `result[i] < i_arg` to `result[i] > i_arg`
- Changed `result.insert(i - 1, i_arg)` to `result.insert(i, i_arg)`

**Usage**:
```bash
ruby 2-sort.rb <numbers...>
```

**Example**:
```bash
ruby 2-sort.rb 12 41 2 9 -9 31 -1 32
# Output: -9 -1 2 9 12 31 32 41 (ascending order)
```

### Task 3: User Password Validation (Python)

**File**: `3-user.py`

**Bugs**:
1. Password setter used wrong attribute name (`self._password` instead of `self.__password`)
2. Case mismatch - setter used `.lower()` but validator used `.upper()`

**Issue**: Password was never stored correctly AND validation always failed.

**Fix**:
- Changed `self._password` to `self.__password` in the setter
- Changed `.upper()` to `.lower()` in the validator for consistency

**Usage**:
```bash
python3 3-user.py
```

**Example**:
```bash
python3 3-user.py
# Output: Test User (no errors means all tests passed)
```

### Task 4: Doubly Linked List Deletion (C)

**File**: `4-delete_dnodeint/delete_dnodeint_at_index.c`

**Bugs**:
1. Wrong pointer assignment: `(*head)->prev->prev = (*head)->prev`
2. Use-after-free vulnerability - accessing freed memory

**Issue**: List corruption, undefined behavior, and potential segmentation faults.

**Fix**:
- Save the next pointer before freeing: `tmp = (*head)->next;`
- Correct pointer connection: `(*head)->prev->next = (*head)->next;`
- Update next node's prev pointer before freeing
- Free the node after saving all necessary pointers

**Usage**:
```bash
cd 4-delete_dnodeint
gcc -Wall -Wextra -Werror main.c delete_dnodeint_at_index.c add_dnodeint_end.c print_dlistint.c free_dlistint.c -o delete_dnodeint
./delete_dnodeint
```

**Example**:
```bash
./delete_dnodeint
# Output: Correctly deletes nodes at specified indices without crashes
```

## Files Modified

1. `/challenge/0-fizzbuzz.py` - Fixed if-elif condition ordering
2. `/challenge/1-print_square.js` - Fixed parseInt radix parameter
3. `/challenge/2-sort.rb` - Fixed comparison operator and insertion index
4. `/challenge/3-user.py` - Fixed attribute name and hash case consistency
5. `/challenge/4-delete_dnodeint/delete_dnodeint_at_index.c` - Fixed pointer logic and memory safety
6. `/challenge/README.md` - Created project documentation

## Requirements

- **Python 3**: For tasks 0 and 3
- **Node.js**: For task 1
- **Ruby**: For task 2
- **GCC**: For task 4 (C compiler with standard flags)

## General Requirements

- All files should end with a new line
- All files are compiled/tested on Ubuntu 20.04 LTS
- Editors: vi, vim, emacs

## Author

Fixed by: codebind
Project: Holberton School - Fix My Code Challenge

## Learning Objectives

This project demonstrates understanding of:
- Control flow and conditional logic
- Type conversion and parsing
- Sorting algorithms and insertion logic
- Object-oriented programming and encapsulation
- Pointer manipulation and memory management
- Debugging across multiple programming languages
