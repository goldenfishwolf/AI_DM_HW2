# Adder_practice

### Model design
At first I use an lstm and four dense, the input of each dense is same as the output of lstm. Of course, the accuracy is only 84%.
Then I start to think that how to improve it.

* Because of the forget rate, lstm will care less about the previous data, but for addition and subtraction, two numbers in the equation are both important. So I replace the lstm with bidirectional lstm, which will make the importance of two number the same.

* When calculating the addition and subtraction, we humans will first calculate one digit and then another. Therefore I insert another lstm between dense layers and the first lstm, the input is the output of the bidirectional lstm repeating four times. It will give the output every input, so there will be four output, and connect to four dense layers respectively. Using this architecture to simulate the way humans do.

* Since the lower digit will affect higher digit (carry digit), therefore the result of the second lstm should go from lower to higher.

### Experiment data:

3 bit digit
Add
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.9001 | 0.9229 | 0.7362 |
| 20 | 0.9812 | 0.9910 | 0.9605 |
| 50 | 1.0000 | 0.9984 | 0.9916 |
| 75 | 1.0000 | 0.9986 | 0.9930 |
| 100 | 1.0000 | 0.9984 | 0.9929 |




3 bit digit
Sub
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.9587 | 0.9562 | 0.8567 |
| 20 | 0.9708 | 0.9850 | 0.9501 |
| 50 | 1.0000 | 0.9994 | 0.9991 |
| 75 | 1.0000 | 0.9999 | 0.9996 |
| 100 | 1.0000 | 0.9998 | 0.9997 |


3 bit digit
Add & Sub
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.9001 | 0.9229 | 0.7362 |
| 20 | 0.9812 | 0.9910 | 0.9605 |
| 50 | 1.0000 | 0.9984 | 0.9916 |
| 75 | 1.0000 | 0.9986 | 0.9930 |
| 100 | 1.0000 | 0.9984 | 0.9929 |



3 bit digit
Add
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.7895 | 0.7067 | 0.1094 |
| 20 | 0.9823 | 0.9614 | 0.8566 |
| 50 | 0.9988 | 0.9789 | 0.9253 |
| 75 | 1.0000 | 0.9947 | 0.9819 |
| 100 | 1.0000 | 0.9946 | 0.9831 |


Analysis:
* The accuracy of addition and subtraction are both 99%, but the accuracy of mixture of addition and subtraction is a little less since the rule is more complicate.
* The accuracy of subtraction is higher than addition is because that for the subtraction, the average number of digits which need to predict is fewer than addition.



3 bit digit
Add & Sub
Training set : 36000
Valid set : 4000
Testing set : 40000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.9737 | 0.9517 | 0.8469 |
| 20 | 0.9940 | 0.9956 | 0.9842 |
| 50 | 0.9987 | 0.9988 | 0.9966 |
| 75 | 1.0000 | 0.9999 | 0.9987 |
| 100 | 1.0000 | 0.9999 | 0.9990 |


3 bit digit
Add
Training set : 54000
Valid set : 6000
Testing set : 20000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.9945 | 0.9969 | 0.9871 |
| 20 | 0.9999 | 0.9998 | 0.9988 |
| 50 | 1.0000 | 0.9999 | 0.9994 |
| 75 | 0.9999 | 0.9992 | 0.9968 |
| 100 | 1.0000 | 1.0000 | 0.9997 |


Analysis:
The more training data the model get, the easier the model to find the rule, therefore te accuracy will become higher.




2 bit digit
Add & Sub
Training set : 180
Valid set : 20
Testing set : 600

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.4278 | 0.4000 | 0.0117 |
| 20 | 0.4500 | 0.5000 | 0.0100 |
| 50 | 0.5981 | 0.4833 | 0.0500 |
| 75 | 0.7574 | 0.5000 | 0.0400 |
| 100 | 0.9315 | 0.4667 | 0.0317 |


2 bit digit
Add & Sub
Training set : 1800
Valid set : 200
Testing set : 6000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.4511 | 0.4500 | 0.0192 |
| 20 | 0.5354 | 0.5317 | 0.0352 |
| 50 | 0.8241 | 0.7267 | 0.2800 |
| 75 | 0.9828 | 0.8550 | 0.5987 |
| 100 | 1.0000 | 0.8950 | 0.7305 |


Analysis:
At first I want to maintain the ratio of training data to whole universal set. However, this action will make the number of training data too small.
Therefore I set the number of training data to one tenth of the 3 digit.
This number of training data is actually more than half of universal set, so I guess that the model should have certain number of data to find te rules. 



4 bit digit
Add & Sub
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.5592 | 0.5606 | 0.0390 |
| 20 | 0.6203 | 0.5967 | 0.0543 |
| 50 | 0.9595 | 0.6824 | 0.1361 |
| 75 | 1.0000 | 0.6846 | 0.1396 |
| 100 | 1.0000 | 0.6833 | 0.1385 |



4 bit digit
Add & Sub
Training set : 36000
Valid set : 4000
Testing set : 40000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.8861 | 0.8833 | 0.6098 |
| 20 | 0.9829 | 0.9595 | 0.8428 |
| 50 | 1.0000 | 0.9860 | 0.9499 |
| 75 | 1.0000 | 0.9885 | 0.9550 |
| 100 | 1.0000 | 0.9885 | 0.9570 |


Analysis:
18000 training data are a little too less for 4 digit, the result is obviously overfitting. Therefore I double the number of training data, and the accuracy become much higher.
Since the ratio of 36000 training data to te universal set is much less than ratio of 3 digits, this result become an evidence which proof that the model just need certain number of data to find te rules.



3 bit digit
Mul
Training set : 18000
Valid set : 2000
Testing set : 60000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.5047 | 0.5029 | 0.0254 |
| 20 | 0.9322 | 0.6163 | 0.0638 |
| 50 | 0.9997 | 0.6493 | 0.1018 |
| 75 | 1.0000 | 0.6468 | 0.0996 |
| 100 | 1.0000 | 0.6480 | 0.0980 |


3 bit digit
Mul
Training set : 54000
Valid set : 6000
Testing set : 20000

| The number of training epochs | Train accuracy | Valid accuracy | Testing accuracy |
| :------: | :------: | :------: | :------: |
| 10 | 0.6982 | 0.6904 | 0.1353 |
| 20 | 0.8056 | 0.7438 | 0.2261 |
| 50 | 0.9871 | 0.7516 | 0.2415 |
| 75 | 0.9995 | 0.7493 | 0.2469 |
| 100 | 1.0000 | 0.7556 | 0.2499 |


Analysis:
The situation of multiply is more strange. Even give the model more data, the result is still overfitting.
I think this is because the architecture of the model is not fit to the rules of multiply. For example, the higher digit and lower digit will affect each other, since the multiply will sum all the result of every digit.

