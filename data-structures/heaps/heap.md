# Heaps

> The (binary) heap data structure is an array object that we can view as a
nearly complete binary tree
>
> The tree is completely filled on all levels except possibly the lowest, which is filled from the
left up to a point


An array A that represents a heap is an object with two attributes:
1. A:length, which (as usual) gives the number of elements in the array
2. A:heap-size, which represents how many elements in the heap are stored within
array A. That is, although A[1 : : A:length] may contain numbers, 
only the elements in A[1 : : A:heap-size], 
where 0  <= A:heap-size <= A:length, are valid elements of the heap.


### PARENT (i)
    return floor(i/2)
Parent procedure can compute i/2 by shifting i right one bit position.


### LEFT(i)
    return (2 * i)
In most computers, the **_LEFT_** procedure can compute 2 * i
in one instruction by simply shifting the binary representation
of i left by one bit position.

### RIGHT(i) 
    return (2 * i) + 1

Similarly, the **_Right_** procedure can compute 2i + 1 by shifting
the binary representation of i and then adding 1 in lower order bit.

## Types of Heaps
1. Max heap
2. Min heap

For **_Heap Sort_** algorithm we make use of Max Heap.

Min Heap is used in priority queue.

### Some basic procedure and how they are used

1. The _MAX-HEAPIFY_ procedure, which runs in O(log n) time, is the 
key to maintain the MAX HEAP property.

2. The _BUILD-MAX-HEAP_ procedure, which runs in O(n) time,
produces a max heap from unordered input array.

3. The _HEAP_SORT_ procedure, which runs in O(n log n) time, sorts
array in place

4. The _MAX-HEAPIFY-INSERT_ , _HEAP-EXTRACT-MAX_ , _HEAP-INCREASE-KEY_,
and _HEAP-MAXIMUM_ procedures, which run O(n), allow the heap data
structure to implement priority queue.


    
    MAX-HEAPIFY(A, i)
        l = LEFT(i)
        r = RIGHT(i)
        if(l <= A.heap-size && A[i] < A[l])
            largest = l
        else largest = i

        if(largest <= A.heap-size && A[largest] < A[r]
            larget = r

        if(largest != i)
            exchange A[largest] with A[i]
            MAX-HEAPIFY(A, largest);

## Building a heap

We can use the procedure MAX-HEAPIFY in a bottom up manner to convert an array 
to max heap.

    BUILD-MAX-HEAP(A)
        A:heap-size = A:length
        for i = A:length/2 downto 1
        MAX-HEAPIFY(A, i)  
### Time complexity

We can compute a simple upper bound on the running time of **BUILD-MAXHEAP** as 
follows. Each call to **MAX-HEAPIFY** costs O(log n) time,
and **BUILDMAX-HEAP** makes O(n) such calls. Thus, 
the running time is O(n log n). This upper bound, though correct,
is not asymptotically tight.

