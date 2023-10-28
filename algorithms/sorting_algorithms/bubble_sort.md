```plaintext
Function BubbleSort(array):
    // Length of the array
    n = Length of array

    // Traverse through all elements in the array
    For i = 0; i < n-1; i++:
        // Flag to optimize and check if any swap happened
        swapped = False

        // Last i elements are already in place, so we don't check them
        For j = 0; j < n-i-1; j++:
            // Traverse the array from 0 to n-i-1
            // Swap if the element found is greater than the next element
            If array[j] > array[j+1]:
                Swap(array[j], array[j+1])
                swapped = True

        // If no elements were swapped in the inner loop, break
        If swapped is False:
            Break

    Return array

Function Swap(x, y):
    // Temporarily store x
    temp = x

    // Swap values
    x = y
    y = temp
    
    // NOTE: This pseudocode Swap function assumes variables are passed by reference.
    // In many languages, parameters are passed by value, so swapping may require
    // a different approach or modifications to the function.
```
