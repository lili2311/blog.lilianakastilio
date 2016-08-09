---
layout: post
title: Technical Code Interview Prep Notes
categories: css javascript java example
---
####Data Structures and Algorithms
####Question 1: How do you reverse a linked list using recursion (Java)?
I found the answer [on this stackoverflow post "Reversing a linked list in Java, recursively"](http://stackoverflow.com/questions/354875/reversing-a-linked-list-in-java-recursively). This can be solved answering the following questions:

1. What is the reverse of ``null`` (the empty list)? ``null``.
2. What is the reverse of a one element list? the element.
3. What is the reverse of an n element list? the reverse of the second element on followed by the first element.

{% codeblock lang:js  %} public ListNode Reverse(ListNode list) {
    // What is the reverse of null (the empty list)? null.
    if (list == null) return null; 

    // What is the reverse of a one element list? the element.
    if (list.next == null) return list; 

    // What is the reverse of an n element list? the reverse of the second element on followed by the first element.
    // so we grab the second element (which will be the last after we reverse it)
    ListNode secondElem = list.next;

    // bug fix - need to unlink list from the rest or you will get a cycle
    list.next = null;

    // then we reverse everything from the second element on
    ListNode reverseRest = Reverse(secondElem);

    // then we join the two lists
    secondElem.Next = list;

    return reverseRest;
}
{% endcodeblock %}

####Question 2: How do you find a length of a linked list?
Traverse through all the elements until you find the last node which points to ```null```.

####Question 3: How do you find the middle of a linked list using only one pass?
1. Maintain two pointers as you traverse through the linked list. 
2. Increment Pointer 1 on every node and only increment Pointer 2 on every 2nd node. 
3. When you reach the end of the list, Pointer 2 will be pointing to the middle of the list.


{% codeblock lang:js  %}public class LinkedListTest {
    public static void main(String args[]) {
    // Creating LinkedList with 4 elements including head
    LinkedList linkedList = new LinkedList();
    LinkedList.Node head = linkedList.head();
    linkedList.add( new LinkedList.Node("1"));
    linkedList.add( new LinkedList.Node("2"));
    linkedList.add( new LinkedList.Node("3"));

    // Finding middle element of LinkedList in single pass
    LinkedList.Node current = head;
    int length = 0;
    LinkedList.Node middle = head;

    while(current.next() != null){
      length++;
      if(length % 2 == 0){
          middle = middle.next();
      }
      current = current.next();
    }

    if(length % 2 == 1){
      middle = middle.next();
    }

    System.out.println("Length of LinkedList: " + length);
    System.out.println("Middle element of LinkedList : " + middle);
  
    } 
}
{% endcodeblock %}


Read more [here](http://javarevisited.blogspot.com/2012/12/how-to-find-middle-element-of-linked-list-one-pass.html#ixzz3SPYQIL5E).

####Question 4: Does a given linked list have a loop?
This is solved similarly to the question above "Question 3: How do you find the middle of a linked list using only one pass?":

1. Maintain 2 pointers as you traverse through the list. 
2. Increment Pointer 1 on every node and only increment Pointer 2 on every 2nd node.
3. If Pointer 1 and Pointer 2 point to the same node, the list has a loop.

####Question 5: An integer array has numbers from 1 to 100, there is a duplicate in the array. Find the duplicate.
1. Add all the numbers stored in the array.
2. Find the expected sum of all the numbers if there were no duplicates. The sum is represented by a formula ``n(n+1)/2``.
3. Subtract the actual sum from the expected sum. The answer is the dulicate number.
4. This works if there is 1 duplicate in the array, for multiple duplicates use a Hash Map, where the number is the key and the the occurence is the value. Any values larger than 1 will reveal the duplicates.

####Question 6: What is the difference between a Stack vs a Queue?
A Stack is ``LIFO (Last In First Out)`` structure and a Queue is a ``FIFO (First In First Out)`` structure.


####Question 7: What is a Binary Search Tree?
They are also sometimes called ordered or sorted binary trees, are a class of data structures used to implement lookup tables and dynamic sets. They store data items, known as keys, and allow fast insertion and deletion of such keys, as well as checking whether a key is present in a tree. In a binary search tree:

1. Every left node is smaller than the root element.
2. Every right node is larger than the root element.
3. There are no duplicates in the binary search tree.

####Question 8: How would you sort and array using a Bubble sort?

Bubble sort is a simple sorting algorithm that repeatedly steps through the list to be sorted, compares each pair of adjacent items and swaps them if they are in the wrong order. Worst Case performance is ``O(n^2)``, best case is ``O(n)``.

1. Start comparing first and second element ``array[0]`` and ``array[1]``.
2. If ``array[0]`` > ``array[1]`` then swap numbers e.g. ``array[0] = array[1]`` and ``array[1] = array[0]``.
3. Repeat with the next two element, ``array[1]`` and ``array[2]`` and so on until you reach the end of the list
4. This is referred as one pass and at the end of first pass largest number is at last.
5. Repeat this comparison again starting from ``array[0]`` but this time going till second last pair only ``array[n - 1]``.

In a Bubble sort we need ``n - 1`` iteration to sort ``n`` elements at end of first iteration largest number is sorted and subsequently numbers smaller than that.


{% codeblock lang:js  %}var array =[13,1,24,56,23,4,3,2,7,9,10,11];

console.log("Sorted Array: " + bubbleSort(array));

function bubbleSort(a){
  var swapped = true;
  for(var i = 0; i < a.length-1; i ++){
    swapped = false;
    for(var j = 0; j < a.length-1; j ++){
      console.log(i +" " + j);
      if (a[j] > a[j+1]){
        var temp = a[j];
        a[j] = a[j+1];
        a[j+1] = temp;
        swapped = true;
      }
    }
    if(swapped === false) return a; // if no swaps have been made, the array is sorted. No need to keep looping.
    }
  return a;
}
{% endcodeblock %}

####Question 9: How would you check if a number is a palindrome?

Using a modulo we can determine if a number is a palindrome:
{% codeblock lang:js  %}var number = 2332; // example number
var orig_num = number; // keep a copy of the original number
var new_num = number; // this number will change as we try to reverse the number without using strings
var check_num = 0;
var check_is_palindrome =[]; // storing all the individual numbers here  as we get them in reverse order.
// console.log("Number to check: " + number);

function isPalindrome(number) {

    if (number === 0) return true;

    var num_of_passes = 0;

    while (new_num > 0){
        num_of_passes ++;
        remainder = number % 10;
        //console.log("Remainder: " + remainder);
        new_num = (number - remainder)/10;
        //console.log("New number: "+ new_num);
        number = new_num;
        check_is_palindrome.push(remainder);
        //console.log(check_is_palindrome);
        //console.log("Num of passes: " + num_of_passes)
    }

    var final_check_num = 0; // this is to save our result after reversing the number

    for (var i = 0; i < check_is_palindrome.length; i++){
        final_check_num += check_is_palindrome[i] * Math.pow(10,num_of_passes - 1);
        num_of_passes --;
        //console.log("Final_check_num: " + final_check_num);
      }
    
    return orig_num === final_check_num;
}

console.log("Is number " + number " a palindrome? " + isPalindrome(number));

{% endcodeblock %}

####Question 10: Describe a Selection Sort?

Selection sort is a sorting algorithm, specifically an in-place comparison sort. It has ``O(n^2)`` time complexity, making it inefficient on large lists. It performs worse than the similar insertion sort. 

1. Divide the list into two parts: the sublist of items already sorted and the sublist of items left to be sorted. Initially, the sorted sublist is empty and the unsorted sublist is the entire input list.
2. Find the smallest or largest element in the unsorted sublist.
3. Exchange places with the leftmost unsorted item.
4. Repeat 2 & 3 until no unsorted items left.


####Question 11: Describe a Shell Sort?

The method starts by sorting pairs of elements far apart from each other, then progressively reducing the gap between elements to be compared. Starting with far apart elements can move some out-of-place elements into position faster than a simple nearest neighbor exchange. It is similar to the Insertion sort that allows the exchange of items that are far apart. Worst case performance is ``O(n^2)``, best case is O``(n log2 n)``. Picking the correct gaps is difficult, they should be reducing until the gap is 1.

####Question 12: Describe an Insertion Sort?

Insertion sort is a simple sorting algorithm that builds the final sorted array (or list) one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

1. For each item, remove form unsorted and place in the correct place in teh sorted list or sub-list
2. Move up all larger elements if required to place the item in the correct place.


####Question 13: Describe a Quick Sort?
This is an efficient sorting algorithm. The steps are:

1. Pick an element, called a pivot, from the array.
2. Reorder the array so that all elements with values less than the pivot come before the pivot, while all elements with values greater than the pivot come after it (equal values can go either way). 
3. After this partitioning, the pivot is in its final position. This is called the partition operation.
4. Recursively apply the above steps to the sub-array of elements with smaller values and separately to the sub-array of elements with greater values.
5. The last element is ussually chosen as the pivot, but this will yeild a wort case complexity on an already sorted array or on an array of identical elements.

{% codeblock lang:js  %}var array = [13,1,24,56,23,4,3,2,7,9,10,11];

console.log("Sorted Array: " + quickSort(array));

function quickSort(a) {
  var answer = [];
  if(a.length === 1) answer=a;
  if (a.length > 1){
    console.log("quicksort " + a);
    var pivot = a[a.length-1];
    //console.log(a.length);
    var left_a = [];
    var right_a = [pivot];
    for(var i = 0; i < a.length; i++){
      //console.log("Comparing " + pivot " and a[i]= " + a[i]);
      if(pivot > a[i]){
        left_a.push(a[i]);
      }
      if(a[i] > pivot){
        right_a.push(a[i]);
      }
      console.log(left_a, right_a);
    }
    answer.push(quickSort(left_a));
    answer.push(quickSort(right_a));
  }
  return answer;
{% endcodeblock %}

####Question 14: Describe a Merge Sort?

A merge sort is an ``O(n log n)`` comparison-based sorting algorithm. Mergesort is a divide and conquer algorithm that was invented by John von Neumann in 1945.
Conceptually, a merge sort works as follows:

1. Divide the unsorted list into ``n`` sublists, each containing 1 element (a list of 1 element is considered sorted).
2. Repeatedly merge sublists to produce new sorted sublists until there is only 1 sublist remaining. This will be the sorted list.

{% codeblock lang:js  %}function merge_sort(list m)
    // Base case. A list of zero or one elements is sorted, by definition.
    if length(m) <= 1
        return m

    // Recursive case. Divide the list into equal-sized sublists.
    var list left, right
    var integer middle = length(m) / 2
    for each x in m before middle
         add x to left
    for each x in m after or equal middle
         add x to right

    // Recursively sort both sublists
    left = merge_sort(left)
    right = merge_sort(right)
    // Then merge the now-sorted sublists.
    return merge(left, right)

function merge(left, right)
    var list result
    while notempty(left) and notempty(right)
        if first(left) <= first(right)
            append first(left) to result
            left = rest(left)
        else
            append first(right) to result
            right = rest(right)
    // either left or right may have elements left
    while notempty(left)
        append first(left) to result
        left = rest(left)
    while notempty(right)
        append first(right) to result
        right = rest(right)
    return result
{% endcodeblock %}


####Question 15: Describe a Heap Sort?

Heap sort is a comparison-based sorting algorithm. Heapsort can be thought of as an improved selection sort.


####HTML, CSS and JavaScript
####Question 1: Explain what are selectors in CSS?
Selectors enable selecting an element to which a style is to be applied. There are different types of selectors, like ``class``, ``id``, ``descendant``, ``type`` selectors.

####Question 2: Explain a CSS box model?
Each element is represented as a rectangular box. Each of these boxes is described using the standard box model. Each box has four edges: the margin edge, border edge, padding edge, and content edge.

There are two types of box model, ``border-box`` and ``content-box``.

####Question 3: What are pseudo classes and what are they used for?

Pseudo classes are similar to classes, but they are not defined in the markup. Some examples are ``:link``, ``:visited``, ``:hover``, ``:active``, ``:first_line``. They are used to call a specific action on an element, for example changng the link colour after it is visited, or changing a link colour when it is hovered.

####Question 4: How do you optimize a website’s assets?
Some of the ways to optimize assets are:

1. Make fewer HTTP requests
2. Use a Content Delivery Network
3. Add an Expires header
4. Gzip components
5. Put CSS at the top
6. Move scripts to the bottom
7. Make JavaScript and CSS external
8. Minify JavaScript
9. Remove duplicate scripts

####Question 5: What are the 3 different ways to apply CSS?

1. Inline
2. External
3. Embedded/Internal

####Question 6: How is the float property implemented in CSS?

Floats allow an element to be positioned horizontally, allowing elements below the floated element to flow around it. Several floating elements can be placed together to make a gallery type layout. To prevent subsequent elements from flowing around the floated element, pass in the clear property, followed by the side you wish to disable (i.e., ‘left’, ‘right’, ‘both’).

####Question 7: What is the purpose of the z-index and how is it used?
The z-index helps specify the stack order of positioned elements that may overlap one another.

####Question 8: What's the difference between standards mode and quirks mode?
One prominent difference between quirks and standards modes is the handling of the CSS Internet Explorer box model bug. Another notable difference is the vertical alignment of certain types of inline content. 

If the browser decides that the document is modern, it’ll render it in standards mode. This means that, as a rule, CSS is applied in accordance with the CSS2 specification.
If the browser decides that the document is old-school, it’ll render it in quirks mode.

####Question 9: Graceful degradation vx progressive enhancement?

Graceful degredation - making sure that everythign still works to some level in an older browser, providing with basic functionality of the site.

Progressive enhancement - starting off with the oldest browsers in mind and adding in better functionality for browsers that can handle it.

Degrading gracefully means looking back whereas enhancing progressively means looking forward whilst keeping your feet on firm ground.

####Useful Resources:

1. [Mozilla Developer Network](https://developer.mozilla.org/).
2. [Wikipedia](http://en.wikipedia.org/wiki/).
3. [StackOverflow](http://stackoverflow.com/).
4. [Tuts+](http://code.tutsplus.com/tutorials/the-30-css-selectors-you-must-memorize--net-16048).
5. [Java Revisited Blog](http://javarevisited.blogspot.com/2012/12/how-to-find-middle-element-of-linked-list-one-pass.html#ixzz3SPYQIL5E).
6. [Quirks Mode](http://quirksmode.org/css/user-interface/boxsizing.html).
7. [Google Developers](https://developers.google.com/speed/articles).
8. [Skilled Up](http://www.skilledup.com/articles/25-css-interview-questions-answers/)
9. [Quirks vs Standard](https://developer.mozilla.org/en-US/docs/Mozilla_Quirks_Mode_Behavior)
10. Excellent resource of [front end interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions#fun-questions).
11. [HTTP2](http://http2.github.io/faq/)