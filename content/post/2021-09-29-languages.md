+++
author = "Alex Nuttall"
date = 2021-09-29
title = "Languages"
+++
After completing a coding bootcamp at [Northcoders](https://northcoders.com/), I'm looking forward to using the time I have before finding a job, or in fact some of my free-time once I have found one, to pursue some learning projects. The freedom to choose a learning path independently of any kind of syllabus feels both exciting and sometimes a bit overwhelming. I would like to learn a new language, but on what basis should I choose?

Presumably many other developers reach this point, having learnt Javascript or some other first language, knowing enough about programming to have an idea of the limitations of that language, but not enough to make a truly informed decision about any particular alternative.

## C#
The solution seems to be to pick one and try it out. I decided to use C# to work on the coding challenges in the [Algorithmic Toolbox](https://www.coursera.org/learn/algorithmic-toolbox) course. This was the first time I had worked with a statically typed language, and I intially ran into some problems working with unfamilar data-types. Beyond that, however, it was nice to find that the basics of the language already felt familiar enough. The words `public static void` finally gained some significance for me.

It's great to get some exposure to C# in this way but I doubt the advantages of a more rigourously structured language will become apparent in the context of small algorithmic code challenges. In this context, C# feels like Javascript 'with extra steps'. Tackling some kind of larger, more structured project will make the advantages more apparent.

By way of example, and to test out my new blog's code highlighting, here are my two solutions to a Codewars kata whose goal is to remove elements from array a which are present in array b while preserving their order.
### JS
```javascript
const arrayDiff = (a, b) => a.filter(e => !b.includes(e))
```
### C#
```c#
using System.Collections.Generic;

public class Kata
{
  public static int[] ArrayDiff(int[] a, int[] b)
  {
    List<int> res = new List<int>();
    for (int i = 0; i < a.Length; i++)
    {
      bool match = false;
      for (int j = 0; j < b.Length; j++)
      {
        if (a[i] == b[j])
        {
          match = true;
        }
      }
      if (!match)
      {
        res.Add(a[i]);
      }
    }
    return res.ToArray();
  }
}
```
You can apparently write one-liners in C# using LINQ, so it's hardly a fair comparison. From what I understand, newer versions of C# increasingly allow users to write concise code.