# Big O & Recursion
---
## Introduction
- Computer Science is a science of tradeoffs
- Faster, less memory, more readable? Well it totally depends on what you're doing.
- BH agrees with Kyle Simpson in that he believes code should be written in a way more for the humans than the computer. Human readable code. Communcation for ther person who comes after, you or others.

Welcome to our workshop! I have to admit, after creating these materials, that completing all this in six hours and really grasping it is ambitious to say the least. This is/can be difficult material and so I would tell you to not be frustrated if you don't get it at first. Remember, students in universities are given semesters to really grasp this.

Which brings me to my next point: it's a bit of a disservice to the great professors out there to say this is four semesters of their classes. While we are drawing from my first four semesters of material, there's a lot of other exercises and materials they go over in college. The title is somewhat of a clickbait title. However, I will say that I believe this material can be distilled down to a shorter and easier to digest level and that's what this class aims to do. This class aims to be a practical intro to CS for those who know JavaScript but have yet to delve into science of programming. This class is a first step.

Really, for any developer, the first and likely last book you need to read is Cormen's Intro to Algorithms (please buy it, it's worth it; thanks MIT.) This book, while not super fun to read, will serve you throughout your entire career. While computers have made leaps and bounds, we're still using the same algorithms and this book will impart that knowledge to you. Just read it, pay the tax, and benefit for the rest of your career! However, in the mean time, this is a good place to start to show that the mental gymnastics of algorithms and data structures are fun. 

## Big O
**Big O is the way we analyze how efficient algorithms (or code in this case)** without getting too mired in the details. We can model how much time any function is going to take given n inputs, but in reality we're interested in the order of magnitude of the number and necessarily of the exact figure.

Example: I don't particularly care if a function takes 300 milliseconds versus 330 milliseconds given 1,000 inputs, but I do care if it takes 300 milliseconds versus 30 seconds. This would be a difference in an order of magnitude, or basically we're saying we only care if the difference is pretty large.

Enter Big O. Think of the O as a vacuum that sucks in all the unimportant information and just leaves you with the important stuff. Let's look at a purely mathematical perspective for a second. Say we have the equation 3x² + x + 1. If we plug in 5, the first term will be 75, the second term will be 5, and the third will be 1. In other words, most of the piece of the pie comes from the first term, to the point we can just ignore the other terms. If we plug in huge numbers, it becomes even more apparent. IE if we do 5,000,000, the first term is 75,000,000,000,000, the second is 5,000,000, and the last 1. A huge gap.

Hence this is what Big O does; we ignore the little parts and concentrate on the big parts. Keeping with 3x² + x + 1, the Big O for this equation would be O(n²) where O is just absorbing all the other fluff (including the factor on the biggest term.) Just grab the biggest term. So for n terms, it's going take us n*n time to go through our inputs. So let's see how to derive this from an algorithm.

```javasript
function crossAdd(input) {
    var answer = [];
    for (var i = 0; i < input.length; i++) {
        var goingUp = input[i];
        var goingDown = input[input.length-1-i];
        answer.push(goingUp + goingDown);
    }
    return answer;
}
``` 

                    

This is O(n) because we go through all the inputs once in a loop.


function find(needle, haystack) {
    for (var i = 0; i < haystack.length; i++) {
        if (haystack[i] === needle) return true;
    }
}

                    

Still O(n). Unless we say otherwise, we're assuming worst case scenario. In this worst case, the needle would be the last element.


function makeTuples(input) {
    var answer = [];
    for (var i = 0; i < input.length; i++) {
        for (var j = 0; j < input.length; j++) {
            answer.push([input[i], input[j]]);
        }
    }
    return answer;
}
                    

This would be O(n²). For every input, we have to go through a full loop inside of another full loop, meaning we're doing a lot of work! This is the trick: look for loops. A loop inside of a loop inside of a loop would likewise be O(n³).

If we have no loops and just do something and exit/return, then it's said we're doing it in constant time, or O(1).

We'll get more into it later, but you can also have O(log n) if a code employs a divide-and-conquer strategy (often recursive,) meaning as you add more terms, the increases in time as you add input diminishes. We'll talk more about that with merge and quick sort.
