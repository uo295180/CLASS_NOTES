
# Basic Concepts

Giving a set of *n* elements and an order relation. Sorting can be influenced by:
- The type
- The size
- The device on which they are

## Classification criteria

- Total number of steps:
	- Complexity
- Number of comparisons performed
- Number of interchanges performed
	- Much more expensive than the comparison
- Stability
- Type of memory used
	- Internal algorithms
	- External algorithms

# Sorting algorithms

## Bubble

It's based on the successive comparison and exchange of adjacent elements. At each step, each element is compared to the previous one. In the first step, the lowest element will be placed in the leftmost position and so on

```Java
public void sort(int[] elements){
	for(int i = 0; i < elements.length; i++){
		for(int j = elements.length - 1; j >= i; j--){
			if(elements[j - 1] > elements[j]){
				Util.interchange(elements, j-1, j);
			}
		}
	}
}
```

>[!Bubble]-
>Simple algorithm
>Sorting by direct exchange
>High number of comparisons and exchanges
>
>Best case: O(n\*\*2)
> Worst case: O(n\*\*2)
> Average case: O(n\*\*2)

## Bubble with sentinel

In the previous example, the last steps are repeated unnecessarily. To avoid it, an stop condition is added. Then, if a pass does not make any change, the list is already sorted

```Java
public void sort(int[] elements){
	boolean hasChanged = true;
	for(int i = 0; i < elements.length; i++){
		if(!hasChanged) break;
		hasChanged = false;
		for(int j = elements.length - 1; j >= i; j--){
			if(elements[j - 1] > elements[j]){
				Util.interchange(elements, j-1, j);
				hasChange = true;
			}
		}
	}
}
```

>[!Bubble with sentinel]-
>Simple algorithm
>Sorting by direct exchange
>High number of comparisons and exchanges
>
>Best case: O(n)
> Worst case: O(n\*\*2)
> Average case: O(n\*\*2)

## Direct Insertion

The vector is divided into two virtual parts: An ordered one and the unordered sequence. In each step we take the first element of the unordered sequence and we insert it into its corresponding place of the ordered sequence.

```Java
public void sort(int[] elements){
	int j;
	int pivot;
	for(int i = 1; i < elements.length; i++){
		pivot = elements[i];
		j = i -1;
		while(j >= 0 && pivot < elements[j]) {
			elements[j+1] = elements[j];
			j--;
		}
		elements[j+1] = pivot;
	}
}
```

>[!Direct insertion]-
>Simple algorithm
>Sorting by insertion
>High number of comparisons and exchanges but less than the bubble method
>
>Best case: O(n)
> Worst case: O(n\*\*2)
> Average case: O(n\*\*2)

## Direct Selection

Consists on selecting the lowest element and exchange it with the first element. Repeat the process until the last element remaining is the biggest one.

```Java
public void sort(int[] elements){
	int posMin;
	for(int i = 0; i < elements.length - 1; i++){
		posMin = Util.findPosMin(elements, i); // O(n)
		Util.interchange(elements, i, posMin);
	}
}
```

>[!Direct selection]-
>Simple algorithm
>Sorting by selection
>Small number of exchanges
>It's predictable: The number of exchanges and comparisons depends on n
>The number of comparisons is very high
>
>Best case: O(n\*\*2)
> Worst case: O(n\*\*2)
> Average case: O(n\*\*2)

## Quicksort

Quicksort is based on **partitioning**. When you partition an item, that item will be in its corresponding position. The goal is to partition all the elements. A good partition element (**pivot**) must be chosen that'll be the median in order to crate a tree. The implementation is recursive

Criteria for choosing a good pivot:
- The median (ideal solution but expensive to compute)
- The first element ("cheap" but a bad choice)
- The last element (same as the first one)
- A random element (statistically not the worst choice but has computational cost)
- The central element (statistically it's not a bad choice)
- A compromise solution (median-of-3)
	- We obtain a sample of 3 elements and calculate the median
	- It does not guarantee anything but it can be a good indicator
	- We choose the first element, the last element and the central element
	- We order the elements, and we assume that the median is the element which is in the center

Idea of the algorithm:
	Repeat until all the elements are sorted $\rightarrow$ O($\log(n)$) ... O($n$)
		Choose a pivot $\rightarrow$ Using median-of-3 is O($1$)
		Partitioning the pivot through a partitioning strategy $\rightarrow$ Typical case O($n$) 

```Java
public class Quicksort implements ISortingAlgorithm{
	@Override
	public void sort(int[] elements){
		quicksort(elements, 0, elements.length-1, 1);
	}
	/*get the position of the median of the three(left, right and
	center) and moves the elements to order them*/
	private int median_of_three(int elements[], int left, int right){
		int center = (left + right)/2;
		if(elements[left] > elements[center])
			Util.interchange(elements, left, center);
		if(elements[left] > elements[right])
			Util.interchange(elements, left, right);
		if(elements[center] > elements[right])
			Util.interchange(elements, center, right);
		return center;
	}
	
	public static void quickSort(int elements[], int left, int right){
		int i = left;
		int j = right - 1;
		int pivot;
		
		if(left < right){//if there's one element it's not necessary
			int center = median_of_three(elements, left, right);
			//if there're less than or equal to 3 elements, they're just ordered
			if((right - left) >= 3){
				pivot = elements[center]; // choose the pivot
				Util.interchange(elements, center, right); //hide the pivot
				
				do{
					while(elements[i] <= pivot && i < right) i++;//first element > pivot
					while(elements[j] >= pivot && j > left) j--;//first element < pivot
					if(i < j) Util.interchange(elements, i, j);
				} while(i < j); // end while
				
				// we set the position of the pivot
				Util.interchange(elements, i, right);
				quickSort(elements, left, i-1);
				quickSort(elements, i+1, right);
			}
	}
	
}
```