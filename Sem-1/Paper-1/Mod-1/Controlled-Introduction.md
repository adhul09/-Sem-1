# Controlled Introduction

## a. What is a prompt?

A **prompt** is the instruction or input given to an AI system to tell it what we want it to do.

A prompt can be a question, a task, or a request — it is how we communicate our requirement to an AI model so that it can generate a relevant response.


## b. Basic prompt structure (task + context)

A basic prompt can contain a **task** and **context**.

- **Task** → What we want the AI to do.
- **Context** → Additional information that helps the AI understand the situation.

Eg:

```text
Explain JavaScript arrays. (Task)
I am a beginner learning JavaScript and already know variables and data types. (Context)
```

## c. Using AI for

**i. Concept explanation**

AI can be used to explain difficult concepts in simpler terms.  
However, the explanation should still be checked when accuracy is important.

**ii. Simple logic understanding**

AI can be used to understand the logic behind simple programs or code.

Eg:
```js
let numbers = [1, 2, 3, 4];

let sum = 0;

for (let i = 0; i < numbers.length; i++) {
  sum += numbers[i];
}

console.log(sum);
```
Explanation:  

```text
The logic is:

numbers contains the values [1, 2, 3, 4].
sum is initialized to 0.
The for loop goes through each element of the array.
sum += numbers[i] adds the current element to sum.
After all elements are added, console.log(sum) prints the final sum.
sum = 0

i = 0 → sum = 0 + 1 = 1
i = 1 → sum = 1 + 2 = 3
i = 2 → sum = 3 + 3 = 6
i = 3 → sum = 6 + 4 = 10

Output:
10

```
## d. Observing incorrect outputs

AI does not always produce correct answers. It can sometimes generate incorrect information, incorrect code or misleading explanations.

For example, AI may:

- Give an incorrect answer to a question
- Produce code containing a logical or syntax error
- Misunderstand the requirements of a problem
- Give outdated or incomplete information
- Provide a confident explanation that is actually wrong

Therefore, AI-generated outputs should be checked and verified, especially when learning concepts or using important information.