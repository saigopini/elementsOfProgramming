#Ch. 5: Arrays
import copy

def copyingArrays(A):
	#creating a reference to array A
	#NOTE: this doesn't actually create a copy
	B = A
	#shallow copy
	S = copy.deepcopy(A)
	S.append("X")
	S[0] = 45
	print(S)
	print(A)

def slicingArrays(A):

	#list[start:end:step]
	# indexes: 0, 1, 2, 3, 4, 5, 6, 7
	# same indexes:	-7, -6, -5, 4, -3, -2, -1 (just with negative numbers)

	print(A[-1]) #print last element
	print(A[:]) #prints entire array
	print(A[3:6]) #grab elements at indexes 3, 4, and 5, 6 is exclusive, 3 is inclusive
				  #start = inclusive, end = exclusive
	print(A[1:]) #prints from start, index 1 to end

	print(A[:-1]) #print from 0 to end exclusive, end is not included
	print("here")
	print(A[-3:]) #prints last three elements


	#step allows us to skip a certain number of values
	print(A[2:-1:2]) #prints out every second value

	#when the step is negative, this prints array in reverse
	print(A[2:-1:-1]) #returns a blank array because our starting is at index 2 and there is no way to go backwards to the end
	print(A[-1:2:-1]) #this works because start is at the end of the array and the end is closer to the front so we can use negative step

	#complete reversed list
	print(A[::-1]) #prints list from beginning to end in reverse

	#creates a copy of an array NOT a reference
	B = A[:]
	print(id(A), id(B)) #these are different values

	#changes the data of A, overwriting over the same object
	A[:] = [1, 2, 3] #changes the data of A, just rewrites over the array, the same object

#5-1: reorder array so even entries come first
def evenFirst(A):
	nextEven, nextOdd = 0, len(A) - 1
	while nextEven < nextOdd:
		if A[nextEven] % 2 == 0:
			nextEven += 1
		else:
			A[nextEven], A[nextOdd] = A[nextOdd], A[nextEven]
			nextOdd -= 1
	return A

#print("even first: " + str(evenFirst([0, 1, 2, 3, 4, 5, 6, 7, 8])))

#5-2: reorder array so that all elements less than the pivot come before the pivot and all elements bigger than pivot come after

#the time complexity: O(n^2)
#the space complexity: O(1)
def theDutchNationalFlag(A):
	length = len(A)
	partition = int(length//2)
	pivot = A[partition]
	print("pivot for the Dutch National Flag: " + str(pivot))
	for i in range(length):
		#look for smaller element
		for j in range (i+1, length):
			if A[j] < pivot:
				A[j], A[i] = A[i], A[j]
	for i in reversed(range(length)):
		#look for larger element than pivot
		for j in reversed(range(i)):
			if A[j] > pivot:
				A[i], A[j] = A[j], A[i]
	return A

#print("the Dutch National Flag: " + str(theDutchNationalFlag([9, 3, 4, 5, 6, 7, 2])))

#the time complexity: O(n)
#the space complexity: O(1)
def theOptimalDutchNationalFlag(A):
	length = len(A)
	partition = int(length//2)
	pivot = A[partition]
	print("pivot for the Dutch National Flag: " + str(pivot))
	start, end = 0, length-1
	for i in range(length):
		if A[i] < pivot:
			A[start], A[i] = A[i], A[start]
			start += 1
	for i in reversed(range(length)):
		if A[i] > pivot:
			A[end], A[i] = A[i], A[end]
			end -= 1

	return A
#print("the Optimal Dutch National Flag: " + str(theOptimalDutchNationalFlag([9, 3, 4, 5, 6, 7, 2])))

def evenFirstOddLast(A):
	#A = 2, 4, 1, 6, 7, 8, 3
	#goal: even should come first, odd last
	left = 0
	right = len(A) - 1
	while left < right: #when left = right that means they are sorted
		if A[left] % 2 == 0: #if A[left] is even, don't do anything, just increment left because it's in the right place
			left += 1
		else: #A[left] is odd
			if A[right] % 2 == 0: #A[right] is even, it is in the right place and left is in the wrong place, so decrement right
				right -= 1
			else: #A[right] is even, wrong place and left is in the wrong place so we have to swap now
				A[right], A[left] = A[left], A[right]
				left += 1
				right -=1
	return A
	'''
	#simplified code

	left = 0
	right = len(A) - 1
	while left < right: #when left = right that means they are sorted
		if A[left] % 2 == 0: #if A[left] is even, don't do anything, just increment left because it's in the right place
			left += 1
		else: #A[left] is odd
			if A[right] % 2 == 1: #A[right] is odd, it is in the wrong place and left is in the wrong place, so we need to swap now
				A[right], A[left] = A[left], A[right]
				left += 1
				
			right -=1
	return A
	'''

print(evenFirstOddLast([2, 4, 1, 6, 7, 8, 3]))

def oddFirst(A):
	#goal: odd should come first, even last
	left = 0
	right = len(A)-1
	while left < right:
		if A[left] % 2 == 1:
			left += 1
		else:
			if A[right] % 2 == 1:
				A[right], A[left] = A[left], A[right]
				left += 1
		right -=1

	return A

print(oddFirst([2, 4, 1, 6, 7, 8, 3]))


def dutchNationalFlagAlgorithm(nums):
	"""
	Given three colors (0, 1, 2) in an array, sort the array so all the colors 
	are in order
	ex: 
										hi
				   low
			input: [1, 0, 1, 0, 2, 1, 2, 0]
				   mid

			output: [0, 0, 0, 1, 1, 1, 2, 2]

	if 

	"""
	#3 pointers--low, mid, high. Low is the value we need to swap with mid and starts at 0.
		#high is the value at the end which we neeed to swap with to mid when it is a 3
	low, mid, high = 0, 0, len(nums)-1
	while mid <= high:
		if nums[mid] == 1:
			mid += 1
		elif nums[mid] == 0:
			nums[mid], nums[low] = nums[low], nums[mid]
			low += 1
			mid += 1
		else:
			nums[mid], nums[high] = nums[high], nums[mid]
			high -= 1
	return nums

print(dutchNationalFlagAlgorithm([1, 0, 1, 0, 2, 1, 2, 0]))

def dutchNationalFlag2(A):
	#all numbers less than pivot should be to the left of the pivot
	#all numbers greater than pivot should be to the right of the pivot
	length = len(A)
	partition = int(length//2)
	pivot = A[partition]
	left = 0
	right = len(A) - 1
	print(pivot)
	while left < right:
		if A[left] < pivot:
			left += 1
		else:
			if A[right] < pivot:
				A[right], A[left] = A[left], A[right]
				left += 1
			right -= 1
	return A


#print(dutchNationalFlag2([2, 4, 1, 6, 7, 8, 3]))

