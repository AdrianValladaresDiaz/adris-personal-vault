Provabilistic Inference algorithm, developed by [[Reverend Thomas Bayes]] to infer the existance of god. 

## Bayes Rule
$$
P(A|B) = \frac{P(B|A)\cdot P(A)}  {P(B)}
$$
Where A and B are events and P(B) != 0
- **P(A|B):** is aconditional probabilit. The probability of event A occurring given that B is true. 
- **P(B|A):** is also a conditional probability: the probability of event B occurring given that Ais true.
- **P(A), P(B):** are the probabilities of observing A and  B respectively without any given conditions.

Plainly explained, we have a prior provability, to which we add test data to get to a posterior provability.

### Example
Let's say cancer occurs in 1% of the population.
There is a test that has a 90% chance of showing positive if the person has cancer (Test has a sensitivity of 0.9) and a 90% chance of showing negative if you do **not** have cancer (Test has a specificity of 0.9)
If you test positive, what is the provability that you have cancer?

#### Intuitive Solution

![[NB_Example_1.excalidraw.svg]]

#### Formal Solution

##### Prior provabilty
$$\begin{gather} 
\text{Prob. has cancer }P(C) = 0.01 \\
\text{Prob not cancer }P(\neg C)=0.99 \\
\text{Prob Pos given they have cancer }P(Pos | C)=0.9 \\
\text{Prob Neg given they have cancer }P(Neg | C)=0.1 \\
\text{Prob Neg given they don't have cancer }P(Neg | \neg C) = 0.9\\
\text{Prob Pos given they don't have cancer }P(Pos | \neg C) = 0.1
\end{gather}$$
##### Posterior provability:
$$
\begin{gather}
\text{Prob has cancer given Pos test: }P(C|Pos) = P(C) \cdot P(Pos|C)\\
\text{Prob does not have cancer given Pos test: }P(\neg C|Pos) = P(\neg C) \cdot P(Pos|\neg C)\\
\end{gather}$$
$$
\begin{gather}
P(C|Pos) = P(C) \cdot P(Pos|C) = 0.01 \cdot 0.9 =0.009 \\
P(\neg C|Pos) = P(\neg C) \cdot P(Pos|\neg C) = 0.99 \cdot 0.1 = 0.099\\
\end{gather}$$
#### Normalization:
The posterior provabilities do not add to 1 $$0.009 + 0.099 = 0.108$$
So we normalize them 
$$
\begin{gather}
P(C|Pos) = 0.009 / 0.108 = 0.0833\\
P(\neg C|Pos) = 0.099 / 0.108 = 0.916 \\
0.0833+0.916 = 1
\end{gather}
$$
##### Direct formula application:
![[NB_Example1_bis.excalidraw.svg]]

### Example 2

We receive mails from two senders, Chris and Sara.  Suppose a prior prob. of 50% for each sender.  We also know the word distribution these senders usually use, like so:

| Word | Chris Prob. | Sara Prob. |
|---|:---:|:---:|
| Love | 0.1 | 0.5 |
| Deal | 0.8 | 0.2 |
| Life | 0.1 | 0.3 |

If we receive a mail that contains words Life and Deal, who is the most provable sender?
$$\begin{gather}
P(C) = 0.5\\
P(S) = 0.5\\
\\
P(C|LD) = \frac{P(LD|C) \cdot P(C)}{P(LD)} = \frac{(0.8 \cdot 0.1) \cdot 0.5}{P(LD)} = \frac{0.04}{P(LD)} 
\\\\
P(S|LD) = \frac{P(LD|S) \cdot P(S)}{P(LD)} = \frac{(0.2 \cdot 0.3) \cdot 0.5}{P(LD)} = \frac{0.03}{P(LD)} 
\end{gather}$$
Without calculating P(LD) we already know Chris is more likely to send this email. But lets normalize to get the provability of each sender.![[NB_Example_2.svg]]
$$\begin{gather}

P(C|LD) = \frac{0.04}{P(LD)} = \frac{0.04}{0.04+0.03} = 0.571
\\\\
P(S|LD) = \frac{0.03}{P(LD)} = \frac{0.03}{0.04+0.03} = 0.428
\end{gather}$$
### Example 3

Same as example 2, but with words "Love Deal"
$$\begin{gather}
P(C) = 0.5\\
P(S) = 0.5\\
\\
P(C|LD) = \frac{P(LD|C) \cdot P(C)}{P(LD)} = \frac{(0.8 \cdot 0.1) \cdot 0.5}{P(LD)} = \frac{0.04}{P(LD)} 
\\\\
P(S|LD) = \frac{P(LD|S) \cdot P(S)}{P(LD)} = \frac{(0.2 \cdot 0.5) \cdot 0.5}{P(LD)} = \frac{0.05}{P(LD)} 
\\\\
P(C|LD) = \frac{0.04}{P(LD)} = \frac{0.04}{0.04+0.05} = 0.444
\\\\
P(S|LD) = \frac{0.03}{P(LD)} = \frac{0.05}{0.04+0.05} = 0.555
\end{gather}$$