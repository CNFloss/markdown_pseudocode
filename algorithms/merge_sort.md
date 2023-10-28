`
Function MergeSort(array):
    // Base case: Single element is always sorted
    If Length of array <= 1:
        Return array

    // Split the array into halves
    mid = Length of array / 2
    leftHalf = array[0 to mid]
    rightHalf = array[mid to end]

    // Recursively sort both halves
    leftSorted = MergeSort(leftHalf)
    rightSorted = MergeSort(rightHalf)

    // Merge the sorted halves
    Return Merge(leftSorted, rightSorted)

Function Merge(left, right):
    result = []

    // Pointers for left and right arrays
    leftPointer = 0
    rightPointer = 0

    // While there are elements in both arrays
    While leftPointer < Length of left AND rightPointer < Length of right:
        If left[leftPointer] <= right[rightPointer]:
            Append left[leftPointer] to result
            Increment leftPointer
        Else:
            Append right[rightPointer] to result
            Increment rightPointer

    // Append any remaining elements from left array
    While leftPointer < Length of left:
        Append left[leftPointer] to result
        Increment leftPointer

    // Append any remaining elements from right array
    While rightPointer < Length of right:
        Append right[rightPointer] to result
        Increment rightPointer

    Return result

// NOTE: Merge Sort is a divide-and-conquer algorithm. It divides the array into halves,
// recursively sorts them, and then merges the sorted halves.
`
