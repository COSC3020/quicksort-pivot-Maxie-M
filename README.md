# Quicksort Pivots

in the lectures I only briefly mentioned strategies for determining a good pivot
for quicksort. The implementation on the slides simply picks the leftmost
element in the part of the array that we consider as a pivot. I also mentioned a
few other ways of picking a good pivot, e.g. randomly.

Median-of-three is also a good way of picking a pivot -- inspect the first,
middle, and last elements of the part of the array under consideration and
choose the median value. Using the probabilities for picking a pivot in a
particular part of the array (in the same way as we did on slide 34), argue
whether this method is more or less (or equally) likely to pick a good pivot
compared to simply choosing the first element. Assume that all permutations are
equally likely, i.e. the input array is ordered randomly.

Your answer must derive probabilities for choosing a good pivot and
quantitatively reason with them.

Add your answer to this markdown file. [This
page](https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions)
might help with the notation for mathematical expressions.

## My Answer, Maxie M. 
**Definition of a "Good Piot"** 
- Before we are able to compare the pivot selection strategies in Quicksort, we first need to understand what a "good pivot" is
- A "good pivot" will split the array into roughly equally sized parts
- If the pivot is near the middle of the sorted array, it will be considered a "good pivot" ($\frac{n}{2}$)

**Strategy 1: Picking Leftmost Element as Pivot** 
- The first element is equally likely to be any value. This is due to the array being randomly ordered
- There is a 50% chance that the first element could fall within the middle half of the array, making it be considered a "good pivot"
- Probablity:
  - Good Pivot: $\frac{1}{2}$ or 50%
  -  Bad Pivot (meaning too small or large): $\frac{1}{2}$ or 50%

**Strategy 2: Medium-of-Three Method** 
- The medium-of-three method will involve picking the median of the first, middle, and last element in the array 
- This strategy reduces the influence of extreme values (i.e., very small or very large)
  
  **Probability Analysis for Median-of-Three**
  - Step 1: Catrgorize Elements
    - L (low) = Elements less than ideal pivot range (middle n2)
    - G (greater) = Elements greater than the ideal pivot range
    - P (pivot) = Elements that fall within the ideal pivot range 
    **Possible Combinations of First, Middle, and Last Elements:**
    - (LLL), (LLP), (LPL), (PLL), (LPG), (PGL), (GLP), (LGP), (PLG), (GPL), (PPP),
      (PPL), (PLP), (LPP), (PPG), (PGP), (GPP), (GGG), (GLL), (LGL) (LLG), (GGP),
      (GPG), (PGG), (GGL), (GLG), (LGG)
    - In total there are 27 possible combinations, due to each position being able
      to be either L, G, or P. 
  - Step 2: Simplified Combinations
    - Due to us wanting to focus on the median of the first, middle, and last
    elements are in the middle half of the array (P). We can pick possible
    combinations that will matter in giving us a good pivot
       - PPP: All three elements will be in the pivot range
       - PPL: Two out of the three elements will be in the pivot range, one is low
       - PPG: Two out of the three elements will be in thee pivot range, one is
         greater
      - LPG: One element is low, one element is in the pivot range, and one element
        is greater
  - Checking if Combination is Within Pivot Range
    | Combo Clacs | In Range? | Combo Calcs | In Range? | Combo Calcs | In Range? |
    |-------------|-----------|-------------|-----------|-------------|-----------|
    | 1. $\text{LLL} = \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 10. $\text{LLP} = \left( \frac{1}{4} \right)^2 \times \frac {1}{2} = \frac{1}{32}$ | yes | 19. $\text{LLG} = \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no |
    | 2. $\text{PPP} = \left( \frac{1}{2} \right)^3 = \frac{1}{8}$ | yes | 11. $\text{PPL} = \left( \frac{1}{2} \right)^2 \times \frac {1}{4} = \frac{1}{16}$ | yes | 20. $\text{PPG} = \left( \frac{1}{2} \right)^2 \times \frac {1}{4} = \frac{1}{16}$ | yes |
    | 3. $\text{GGG} = \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 12. $\text{GGP} =  \left( \frac{1}{4} \right)^2 \times \frac {1}{2} = \frac{1}{32}$ | yes | 21. $\text{GGL} =  \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no |
    | 4. $\text{PLL} = \frac{1}{2} \times \left( \frac{1}{4} \right)^2 = \frac{1}{32}$ | yes | 13. $\text{GLL} =  \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 22. $\text{LPG} = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = \frac{1}{32}$ | yes|
    | 5. $\text{LPP} = \frac{1}{4} \times \left( \frac{1}{2} \right)^2 = \frac{1}{16}$ | yes | 14. $\text{GPP} = \frac{1}{4} \times \left( \frac{1}{2} \right)^2 = \frac{1}{16}$ | yes | 23. $\text{PLG} = \frac{1}{2} \times \left( \frac{1}{4} \right)^2 = \frac{1}{32}$ | yes |
    | 6. $\text{PGG} =  \frac{1}{2} \times \left( \frac{1}{4} \right)^2 = \frac{1}{32}$ | yes | 15. $\text{LGG} =  \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 24. $\text{GPL} = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = \frac{1}{32}$ | yes|
    | 7. $\text{LPL} = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = \frac{1}{32}$ | yes | 16. $\text{LGL} =  \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 25. $\text{LGP} = \left( \frac{1}{4} \right)^2 \times \frac{1}{2} = \frac{1}{32}$ | yes |
    | 8. $\text{PLP} = \frac{1}{2} \times \frac{1}{4} \times \frac{1}{2} = \frac{1}{16}$ | yes | 17. $\text{PGP} = \frac{1}{2} \times \frac{1}{4} \times \frac{1}{2} = \frac{1}{16}$ | yes | 26. $\text{PGL} = \frac{1}{2} \times \left( \frac{1}{4} \right)^2 = \frac{1}{32}$ | yes |
    | 9. $\text{GPG} = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = \frac{1}{32}$ | yes| 18. $\text{GLG} = \left( \frac{1}{4} \right)^3 = \frac{1}{64}$ | no | 27. $\text{GLP} = \left( \frac{1}{4} \right)^2 \times \frac{1}{2} = \frac{1}{32}$ | yes |

    - Anaylzing the Table Above:
      
      **Combinations resulting in $\frac{1}{8}$**
      - PPP ($\times {1}$)
        
      **Combinations Resulting in $\frac{1}{16}$**
        | LPP | GPP |
        |-----|-----|
        | PLP | PGP |
        | PPL | PPG |
        - There are 3 combinations for two P's and one L ($\times {3}$)
        - There are 3 combinations for two P's and one G ($\times {3}$)

      **Combinations Resulting in $\frac{1}{32}$**
        | LPL | LLP | LPG | LGP |
        |-----|-----|-----|-----|
        | GPG | GGP | GPL | GLP |
        | PLL | PGG | PLG | PGL |
        - There are six combinations resulting in $\frac{1}{32}$ ($\times {6}$)

      **Combinations Resulting in $\frac{1}{64}$ (Out Of Range)**
        | LLL | GGG |
        |-----|-----|
        | LGG | GLL |
        | LGL | GLG |
        | LLG | GGL |
        - There are six combinations which are out of range of the pivot 
    
  - Calculating the Probability of Selecting a Good Pivot
    - The probability will be calculated based on how many elements fall into the
      L, P, and G categories in each combination
    - Probability of PPP
      - $\text{Probability}(PPP) = \left( \frac{1}{2} \right)^3 = \frac{1}{8} \times {1} = \frac{1}{8}$
    - Probability of PPL
      - $\text{Probability}(PPL) = \left( \frac{1}{2} \right)^2 \times \frac{1}{4} = \frac{1}{16} \times {3} = \frac{3}{16}$
    - Probability of PPG
      - $\text{Probability}(PPG) = \left( \frac{1}{2} \right)^2 \times \frac{1}{4} = \frac{1}{16} \times {3} = \frac{3}{16}$
    - Probability of LPG
      - $\text{Probability}(LPG) = \frac{1}{4} \times \frac{1}{2} \times \frac{1}{4} = \frac{1}{32} \times {6} = \frac{6}{32} = \frac{3}{16}$
  - The Total Probability of a Good Pivot
    - The total probability of a good pivot is determined by the sum of the
      probabilities which were calculated above: 
    - $\text{Total Probability} = \frac{1}{8} + \frac{3}{16} + \frac{3}{16} + \frac{3}{16} = \frac{11}{16} = 0.6875$ or 68.75%

**Conclusion** 

After analyzing both strategies, Picking leftmost element and median-of-three method, and calculating the probabilities, it is clear that the median-of-three method is the most efficient method to use on QuickSort. The chance of selecting a good pivot using the leftmost element is 50%, whereas the chances of selecting a good pivot using the median-of-three method is 68.75%. Leading to the conclusion that the median-of-three method is the more effective strategy to implement for selecting a good pivot. This is due to the array being split evenly will be increased with this method, allowing an increased chance of getting a good pivot.

## Plagiarism Statement: 
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.

## Resources:
**Repositories: used as reference in order to better understand exercise** 
- quicksort-pivot-Powerfuljackell
- quicksort-pivot-IshitaPatel18

