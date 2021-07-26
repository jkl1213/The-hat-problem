### The-hat-problem
I recently came across a youtube video trend popularized by Jubilee where a person is asked to match personal traits to n strangers. 
Eg. Match 6 pets to 6 owners, match 12 star signs to 12 people, etc.

This problem is basically the same as the classic hat problem where n people throw their hats up in the air and the hats land randomly on the people's heads.
Here I try to visualise the probability distribution and thereby compute the p-values of the distinguishing power of people by seeing how many they get right when they are asked to match n items to n strangers.

### For the 12 people case, we have the following probability density function
```
import numpy as np

prob = []
n = 120
for k in range(n+1):
    arr = []
    for j in range(n-k+1):
        arr.append((-1)**j/np.math.factorial(j))
    arr = np.array(arr)
        
    prob.append((1/np.math.factorial(k))*np.sum(arr))
  
 ```    
 ### The probability density function is plotted
 ```
import matplotlib.pyplot as plt
x = np.arange(n+1)
y = np.array(prob)
plt.bar(x, y, color='grey');
plt.title("Probability distribution of number of correct guesses in 12 people");
```
<img width="551" alt="Screenshot 2021-07-26 at 7 18 11 PM" src="https://user-images.githubusercontent.com/79690350/126980592-95aee735-57ac-4670-9062-9221215bf6ff.png">

### The p-value of getting at least 3 people right is therefore 8%

```
np.sum(y[3:])
```

