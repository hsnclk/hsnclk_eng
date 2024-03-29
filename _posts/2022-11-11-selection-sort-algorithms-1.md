---
title: "Algorithms Part 1 - Selection Sort"
comments: false
excerpt: "In this section, I am going to explain what the selection sort algorithm is and how its performance behaves in worst, best and average case scenario"
header:
  #teaser: "/assets/images/2022-11-11-selection-sort-algorithms-1/selection-sort.png"
  #og_image: /assets/images/page-header-og-image.png
  #og_image: /assets/images/2022-11-11-selection-sort-algorithms-1/selection-sort.png
  teaser: "/assets/images/svg-book7.svg"
  og_image: /assets/images/svg-book7.svg
  overlay_image: /assets/images/svg-book7.svg
  overlay_filter: 0.3 #rgba(255, 0, 0, 0.5)
  caption: "background by [SVGBackgrounds.com](https://www.svgbackgrounds.com/)"

  #cta_label: "More Info"
  #cta_url: "https://unsplash.com"
categories:
  - algorithms
tags:
  - algorithms
  - selection Sort algorithm
last_modified_at: 2022-12-29T15:12:19-04:00
toc: true
toc_sticky: true
toc_label: "CONTENT"
#mathjax: true
#classes: wide
---



**IMPORTANT :** The notes that I took for myself. I hope they will help you too.. Each resource that I used is added as reference at the end of the page.
{: .notice}

## Selection Sort

The following card game simply explains how the **selection sort algorithm** works. The game is very simple; we want to sort the **scattered cards** <u>from smallest to largest</u> by comparing them with each other.

To do this; first we need to start with the element in the **first position** and compare this element with other elements to find the **smallest** element. In this situation, our first item will be our **reference value**, as it will be replaced with the smallest item in the list, if any. <u>Anyway, if we find the smallest element in the part of the list other than the first position, we need to <b>swap</b> it with the first element(of course if this value found is less than the first item!).</u> After placing the smallest item in the list in the first position, we will continue the similar operations starting from position 2. In this case, our reference becomes the **2nd** item. After the comparison and, if any, displacement operations are finished, we need to continue the similar operations until the **penultimate** element of the list, respectively. In summary, this is how the selection sort algorithm works.

<!-- <div class="notice--warning" markdown="1">
<h4 class="no_toc"><i class="fas fa-comment"></i> Note:</h4>
---
If you want to see how the algorithm works step by step, you can press the **STEP** button.

Or click the **PLAY** button to run the game by itself.

Finally, if you want to shuffle the cards again and restart the game, you can press the **SHUFFLE** button.

</div> -->

<!-- <img src="{{ site.url }}{{ site.baseurl }}/assets/images/2022-11-11-algorithms-part1-selection-sort/card.gif" srcset="{{ site.url }}{{ site.baseurl }}/assets/images/2022-11-11-algorithms-part1-selection-sort/card-small.gif 480w, {{ site.url }}{{ site.baseurl }}/assets/images/2022-11-11-algorithms-part1-selection-sort/card.gif 1080w" sizes="50vw" width="420px" height="100%" class="align-center" loading="lazy" alt="Selection Sort Algorithm"> -->

<video autoplay loop muted playsinline width="380px" height="100%" class="align-center" title="Selection Sort Algorithm" poster="/assets/images/2022-11-11-selection-sort-algorithms-1/poster.png">
  <source src="{{ site.url }}{{ site.baseurl }}/assets/images/2022-11-11-selection-sort-algorithms-1/selection-sort.webm" type="video/webm">
  <source src="{{ site.url }}{{ site.baseurl }}/assets/images/2022-11-11-selection-sort-algorithms-1/selection-sort.mp4" type="video/mp4">
</video>

<!-- <iframe sandbox="allow-popups allow-same-origin allow-scripts allow-top-navigation" src="https://www.khanacademy.org/computer-programming/program/4808854910533632/embedded?embed=yes&amp;author=no&amp;editor=no&amp;width=688&amp;buttons=no&amp;settings=%7B%22sortType%22%3A%22selection%22%7D" class="perseus-scratchpad" allowfullscreen="" style="height: 450px; width: 100%; border-top-width: 0px;
border-right-width: 0px;
border-bottom-width: 0px;
border-left-width: 0px;" title="Selection Sort Algorithm"></iframe> -->

### An Example of Selection Sort

For example we have an unsorted list like this;

<span style="black: blue"><b>9 - 4 - 3 - 1</b></span>
{: .text-left}

#### Our purpose

Sort numbers from smallest to largest by comparing them with each other.

#### How to apply selection sort algorithm
---

```java
public class SelectionSort {
    public static void main(String[] args) {
        int[] list = {9,4,3,1};
        for(int i=0; i< list.length-1; i++) {
            boolean hasSmallestBeenFounded = false;
            int smallest = i;
            for(int j=i; j< list.length-1; j++){
                if (list[j + 1] < list[smallest]) {
                    smallest = j + 1;
                    hasSmallestBeenFounded = true;
                }
            }
            if(hasSmallestBeenFounded){
                int tempValue = list[i];
                list[i] = list[smallest];
                list[smallest] = tempValue;
            }
        }
//       Arrays.stream(list)
//      .forEach(value -> System.out.print(value + " - "));
    }
}
```

---

1. I need two **nested for loops** to apply the **selection sort** to my list(of course not necessary to use for loop). My **outer loop** starts from the beginning of the list, keeping track of <u>the position I want to hold</u>(that is, it becomes our reference value according to the definition above). At the very beginning of the algorithm, this position is of course "**0**". On the other hand, my **inner for loop** checks the other items other than the item in the position that the outer loop holds **to find the smallest item**.  
2. For each new smallest value found, int "**smallest**" value will be updated throughout the inner for loop.
3. You will notice that the values for "**smallest**" and "**hasSmallestBeenFounded**" are updated just before you get inside the inner for loop. Because the purpose of the inner for loop is to find the smallest value and compare it with the reference value. If we go outside of the inner loop, we reset these two values to find the next smallest value, assuming that these values have fulfilled their task.
4. When the inner "for loop" finishes its execution, the boolean value "**hasSmallestBeenFounded**" is marked as `true`, even if at least one smallest value is found. Because the value of **smallest** can change during the inner loop. If the smallest value is not found, the value "**hasSmallestBeenFounded**" remains `false` and is not entered into the "**if**" statement outside the loop.
5. There is an "**if**" statement inside in the inner loop, **if (list[j + 1] < list[smallest])**. Here, **smallest**, which is supposed to represent the smallest value, is compared with the values at position "**j + 1**" followed by the inner loop. If the value pointing to the "**j+1**" position is smaller than the current "**smallest**" value, we update this "**smallest**" value with the value representing the "**j+1**" position. You can think of **smallest** as a temporary smallest value.
6. If the inner loop finds even one smallest value, it enters the **if statement** outside the inner loop, which replaces the smallest value found with the value in the first position(which is of course the position that I hold via outer loop).
7. After the first position of my outer loop is replaced by the smallest value(if any), we repeat the same process with the 2nd position of my outer loop by increasing the **i** number by **one**. Then, the same operations continue until the **penultimate position(list.length-1)** of my outer loop.

---

<div class="notice--warning" markdown="1">
<h4 class="no_toc"><i class="fas fa-comment"></i> Note:</h4>
---
If you want to run the code in the online tool step by step, you can click the link below.

[link](https://pythontutor.com/visualize.html#code=public%20class%20SelectionSort%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20int%5B%5D%20list%20%3D%20%7B9,4,3,1%7D%3B%0A%20%20%20%20%20%20%20%20for%28int%20i%3D0%3B%20i%3C%20list.length-1%3B%20i%2B%2B%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20boolean%20hasSmallestBeenFounded%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20int%20smallest%20%3D%20i%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%28int%20j%3Di%3B%20j%3C%20list.length-1%3B%20j%2B%2B%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20%28list%5Bj%20%2B%201%5D%20%3C%20list%5Bsmallest%5D%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20smallest%20%3D%20j%20%2B%201%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20hasSmallestBeenFounded%20%3D%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20if%28hasSmallestBeenFounded%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20int%20tempValue%20%3D%20list%5Bi%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20list%5Bi%5D%20%3D%20list%5Bsmallest%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20list%5Bsmallest%5D%20%3D%20tempValue%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D&cumulative=false&curInstr=2&heapPrimitives=nevernest&mode=display&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false)

In the code above, I just used one list instead of using both sorted and unsorted list. That is, I reached the solution by sorting a single list within itself. If you want, you can divide it 2 sublist like that;

| Sorted sublist | Unsorted sublist | Smallest element in unsorted list |
|:--------|:-------:|--------:|
| ()   | (9,4,3,1)   | 1   |
| (1)   | (9,4,3)   | 3   |
| (1,3)   | (9,4)   | 4   |   
| (1,3,4)   | (9)   | 9   |   
| (1,3,4,9)   | ()   |    |   
{: rules="groups"}

</div>

<!-- But sometimes embedded code may crash due to **massive traffic overload**, if you cannot see the code properly, you can click the  -->

<!-- <iframe width="100%" height="800" frameborder="0" src="https://pythontutor.com/iframe-embed.html#code=public%20class%20SelectionSort%20%7B%0A%20%20%20%20public%20static%20void%20main%28String%5B%5D%20args%29%20%7B%0A%20%20%20%20%20%20%20%20int%5B%5D%20list%20%3D%20%7B9,4,3,1%7D%3B%0A%20%20%20%20%20%20%20%20int%20smallest%20%3D%200%3B%0A%20%20%20%20%20%20%20%20int%20firstPosition%20%3D%200%3B%0A%20%20%20%20%20%20%20%20boolean%20hasSmallestBeenFounded%20%3D%20false%3B%0A%20%20%20%20%20%20%20%20for%28int%20i%3D0%3B%20i%3C%20list.length-1%3B%20i%2B%2B%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20hasSmallestBeenFounded%3Dfalse%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20smallest%20%3D%20i%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20for%28int%20j%3Di%3B%20j%3C%20list.length-1%3B%20j%2B%2B%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20if%20%28list%5Bj%20%2B%201%5D%20%3C%20list%5Bsmallest%5D%29%20%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20smallest%20%3D%20j%20%2B%201%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20hasSmallestBeenFounded%20%3D%20true%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%20%20%20%20if%28hasSmallestBeenFounded%29%7B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20firstPosition%20%3D%20list%5Bi%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20list%5Bi%5D%20%3D%20list%5Bsmallest%5D%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20%20list%5Bsmallest%5D%20%3D%20firstPosition%3B%0A%20%20%20%20%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%20%20%20%20%7D%0A%20%20%20%20%7D%0A%7D&codeDivHeight=1100&codeDivWidth=510&cumulative=false&curInstr=2&heapPrimitives=nevernest&origin=opt-frontend.js&py=java&rawInputLstJSON=%5B%5D&textReferences=false"> </iframe> -->

## What is the Time Complexity of Selection Sort?

The time efficiency of selection sort is quadratic.

### Best Case Time Complexity of Selection Sort

*O(n<sup>2</sup>)* comparisons, *O(1)* swaps.

In best case time complexity, we consider the list already sorted. So *O(n)* is **1** as there will be **no** swapping. But to find out whether the list is ordered or not, it would be <u>comparison</u> in any case. This brings a <u>quadratic</u> time complexity with it, that is, *O(n<sup>2</sup>)*. Because we have **2** nested **for** loops.

### Worst Case Time Complexity of Selection Sort

*O(n<sup>2</sup>)* comparisons, *O(n)* swaps.

Software engineers usually concentrate on finding only the <u>worst-case running time</u>, that is, the longest running time for any input of size "**n**". Just like in the best case time complexity, the <u>comparison</u> takes place in <u>quadratic</u> time complexity. But in the worst case scenario, our list of course will <u>not be sorted</u>. Because the worst-case scenario requires it. So the <u>swapping</u> takes place in *O(n)* time.

### Average Case Time Complexity of Selection Sort

*O(n<sup>2</sup>)* comparisons, *O(n)* swaps.

Even if the number of steps in the average time is <u>half</u> of the worst case, the result will still be the same as the worst case since constants will not be taken into account in the formulation.


<div class="notice--warning" markdown="1">
<h4 class="no_toc"><i class="fas fa-comment"></i> Note:</h4>
---
The **worst-case running time** of an algorithm gives us an **upper bound** on the running time for any input. Knowing it provides a guarantee that the algorithm will never take any longer.

Also, when describing the best, worst, and average case time complexities, the **dominant term** is always taken into account, even if we express it as *O(n<sup>2</sup>)* comparisons, *O(n)* swaps. So;

The dominant term of *O(n<sup>2</sup>)* comparisons, *O(n)* swaps --> *O(n<sup>2</sup>)*

</div>

## Reference:

* [selection sort pseudocode](https://www.khanacademy.org/computing/computer-science/algorithms/sorting-algorithms/a/selection-sort-pseudocode)
* [selection sort wiki](https://en.wikipedia.org/wiki/Selection_sort)
* [Introduction to Algorithms third edition](https://en.wikipedia.org/wiki/Introduction_to_Algorithms)
