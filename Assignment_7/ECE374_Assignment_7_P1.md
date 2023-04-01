# ECE374 Assignment 7

03/29/2023

***Group & netid***

**Chen Si**  	**chensi3**

**Jie Wang** 		**jiew5**

**Shitian Yang** 	**sy39**

## P1: Topological Sort on Language

![image-20230329220527198](./ECE374_Assignment_7_P1.assets/image-20230329220527198.png)

### Solution:

#### Intuition

To efficiently identify the order of the symbols in Σ using the given list D[n] of words, we can apply topological sort on a directed graph.

1. Initialize an empty directed graph G with nodes for each unique character in Σ.
2. Iterate through the list D[n], comparing adjacent words. For each pair of adjacent words, find the first character that differs between the two words.
3. Create a directed edge in the graph G from the differing character in the first word to the differing character in the second word. This edge indicates that the first character comes before the second character in the lexicographic order.
4. Perform a topological sort on the directed graph G. This will provide a linear ordering of the nodes in the graph, which corresponds to the lexicographic order of the characters in Σ.

#### Algorithm:

```python
from collections import defaultdict, deque

def create_graph(alphabet, words):
    graph = {char: set() for char in alphabet}
    for i in range(len(words) - 1):
        word1, word2 = words[i], words[i+1]
        for char1, char2 in zip(word1, word2):
            if char1 != char2:
                graph[char1].add(char2)
                break
    return graph

def topological_sort(graph):
    visited = set()
    sorted_chars = deque()
    
    def visit(char):
        if char not in visited:
            visited.add(char)
            for neighbor in graph[char]:
                visit(neighbor)
            sorted_chars.appendleft(char)
            
    for char in graph:
        visit(char)
        
    return ''.join(sorted_chars)

def find_lexicographic_order(alphabet, words):
    graph = create_graph(alphabet, words)
    return topological_sort(graph)

alphabet = {'Q', 'X', 'Z'}
words = ['QQZ', 'QZZ', 'XQZ', 'XQX', 'XXX']
order = find_lexicographic_order(alphabet, words)
print(order)

```

#### Time Complexity

Because

graph + top





### Reference

> 1. lexicographic order: 
>
> Also known as dictionary order, or alphabetical order, is a method of ordering a set of strings or sequences based on the order of individual elements within the sequences. This order is usually based on an underlying order of the elements' alphabet or set.
>
> 在英文字典中，排列单词的顺序是先按照第一个字母以升序排列（即a、b、c……z 的顺序）；如果第一个字母一样，那么比较第二个、第三个乃至后面的字母。如果比到最后两个单词不一样长（比如，sigh 和 sight），那么把短者排在前。
>
> 通过这种方法，我们可以给本来不相关的单词强行规定出一个顺序。“单词”可以看作是“字母”的[字符串](https://zh.wikipedia.org/wiki/字符串)，而把这一点推而广之就可以认为是给对应位置元素所属集合分别相同的各个有序[多元组](https://zh.wikipedia.org/wiki/元组)规定顺序：下面用形式化的语言说明。
>
> 2. Lab14
> 3. 
