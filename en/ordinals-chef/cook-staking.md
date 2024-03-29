# 👩‍🍳 Cook Staking

## Rules

\
The rules of the game are straightforward: every **5,000 $COOK** **STAKING** will equal one entry ticket for the prize draw.

The ticket numbers will be displayed on RuneAlpha before the appearance of the end block.\


**Snapshot Period:**

* **Start Block:** TBA
* **End Block:** TBA



## Selection Process

The selection process for determining winners is carefully designed to ensure fairness and randomness, leveraging blockchain technology. Here is a step-by-step guide to our selection algorithm:

#### Pre-Event Announcement

* The **End Block** to determine the winner(s) will be announced before the event.

#### Initial Winner Selection

* Extract the last 8 characters of the hash from the **End Block**.
* Convert these 8 characters into a decimal number, denoted as `s`.
* Calculate the index of the first winning ticket as `index_1 = s mod n`, where `n` is the initial total number of tickets.
* Remove the winning ticket from the list, decreasing the total ticket count by 1.

#### Subsequent Winner Selections

For each subsequent winner `i` (starting from the second winner):

1. Use the last 5 characters of the previous winner's address.
2. Convert these 5 characters into a decimal number, `s_i`.
3. Calculate the index of the winning ticket as `index_i = s_i mod (n - (i-1))`, where `n - (i-1)` reflects the updated total number of tickets after removing winners.
4. Remove the winning ticket from the list, continuing to adjust the total ticket count for each selection.

#### Repeat the Process

* Continue the process, using the last 8 characters of the most recent winner's address to select the next winner.
* Repeat until all desired tickets are picked or no tickets remain.\


#### Example:

* Let's say the End Block will be 834200 Its blockhash will be:  \
  [https://mempool.space/block/000000000000000000001b95867e0182e85e74313cf5b6b1080fe762634b70dd](https://mempool.space/block/000000000000000000001b95867e0182e85e74313cf5b6b1080fe762634b70dd)
* Total valid tickets: **888**\
  \
  **Select first winner:**
* Extract the last 8 characters of the hash code: `634b70dd`
* Convert `634b70dd` to a decimal number: **1665888477**
* Perform the operation: **1665888477 mod 888** = **477**
* Therefore, ticket number **477** is the first ticket selected.\
  \
  The wallet address associated with ticket number 477 will serve as the basis (or 'seed') for determining the next winner\
  This procedure will be repeated, using each new winner's wallet address as the seed for the subsequent selection, until a total of 333 winners have been chosen.

