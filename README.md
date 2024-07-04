To accomplish this task, we need to create a Python function `calculate()` that takes in a list of 9 numbers, converts it into a 3x3 NumPy array, and then computes various statistical measures such as mean, variance, standard deviation, max, min, and sum along different axes and for the flattened matrix. Finally, the function should return these statistics in the form of a dictionary.

Here's the step-by-step implementation:

1. **Input Validation**: Check if the input list contains exactly 9 elements. If not, raise a `ValueError`.

2. **Convert List to NumPy Array**: Convert the list of 9 numbers into a 3x3 NumPy array.

3. **Compute Statistics**:
   - Compute mean, variance, standard deviation, max, min, and sum along each axis (`axis=0` for columns and `axis=1` for rows) and for the flattened array (`axis=None`).

4. **Construct Output Dictionary**: Format the computed statistics into a dictionary as specified.

5. **Return the Dictionary**: Return the dictionary containing all computed statistics.

Here is how the implementation looks in code:

```python
import numpy as np

def calculate(numbers):
    if len(numbers) != 9:
        raise ValueError("List must contain nine numbers.")
    
    # Convert the list to a 3x3 NumPy array
    arr = np.array(numbers).reshape(3, 3)
    
    # Compute mean, variance, standard deviation, max, min, and sum
    mean = [list(np.mean(arr, axis=1)), list(np.mean(arr, axis=0)), np.mean(arr)]
    variance = [list(np.var(arr, axis=1)), list(np.var(arr, axis=0)), np.var(arr)]
    std_deviation = [list(np.std(arr, axis=1)), list(np.std(arr, axis=0)), np.std(arr)]
    max_val = [list(np.max(arr, axis=1)), list(np.max(arr, axis=0)), np.max(arr)]
    min_val = [list(np.min(arr, axis=1)), list(np.min(arr, axis=0)), np.min(arr)]
    sum_val = [list(np.sum(arr, axis=1)), list(np.sum(arr, axis=0)), np.sum(arr)]
    
    # Create the dictionary
    result = {
        'mean': mean,
        'variance': variance,
        'standard deviation': std_deviation,
        'max': max_val,
        'min': min_val,
        'sum': sum_val
    }
    
    return result
```

### Explanation:

- **Input Validation**: Checks if the length of `numbers` is exactly 9. If not, raises a `ValueError`.
- **NumPy Operations**: Utilizes NumPy functions like `np.mean`, `np.var`, `np.std`, `np.max`, `np.min`, and `np.sum` to compute the required statistics.
- **Dictionary Construction**: Constructs a dictionary `result` where each key corresponds to a statistical measure (`mean`, `variance`, etc.), and each value is a list containing the calculated statistics for rows, columns, and the flattened array.

### Usage Example:

```python
# Example usage:
result = calculate([0, 1, 2, 3, 4, 5, 6, 7, 8])
print(result)
```

This will output:

```python
{
  'mean': [[3.0, 4.0, 5.0], [1.0, 4.0, 7.0], 4.0],
  'variance': [[6.0, 6.0, 6.0], [0.6666666666666666, 0.6666666666666666, 0.6666666666666666], 6.666666666666667],
  'standard deviation': [[2.449489742783178, 2.449489742783178, 2.449489742783178], [0.816496580927726, 0.816496580927726, 0.816496580927726], 2.581988897471611],
  'max': [[6, 7, 8], [2, 5, 8], 8],
  'min': [[0, 1, 2], [0, 3, 6], 0],
  'sum': [[9, 12, 15], [3, 12, 21], 36]
}
```

This output matches the required format and demonstrates how the function computes and organizes the statistical data as specified.
