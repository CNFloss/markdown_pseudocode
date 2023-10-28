`
Function BinarySearch(array, target):
    // Define initial low and high pointers
    low = 0
    high = Length of array - 1

    // Continue searching while the range has elements
    While low <= high:
        // Calculate the middle index
        mid = (low + high) / 2
        
        // If the target is found at the middle index, return the index
        If array[mid] == target:
            Return mid

        // If the target is less than the element at the middle index, search the left half
        ElseIf target < array[mid]:
            high = mid - 1

        // Otherwise, search the right half
        Else:
            low = mid + 1

    // If the loop finishes without finding the target, return an indication that it's not in the array
    Return -1

// NOTE: This pseudocode assumes the array is sorted in ascending order.
// The BinarySearch function returns the index of the target if found, or -1 if not found.
`
