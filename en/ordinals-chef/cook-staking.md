# 👩‍🍳 Cook Staking

## Rules

\
The rules of the game are straightforward: every **5,000 $COOK** **STAKING** will equal one entry ticket for the prize draw.

The ticket numbers will be displayed on RuneAlpha before the appearance of the Root block.\


**Snapshot Period:**

* **Start Block:** 837669
* **End Block:** 838669



## Selection Process

The selection process for determining winners is carefully designed to ensure fairness and randomness, leveraging blockchain technology. Here is a step-by-step guide to our selection algorithm:

#### Pre-Event Announcement

* The **Root Block** to determine the winner(s) will be announced before the event.

#### Initial Winner Selection

* Extract the last 9 characters of the hash from the **Root Block**
* Convert these 9 characters into a decimal number, denoted as `s`.
* Calculate the index of the first winning ticket as `index_1 = s mod n`, where `n` is the initial total number of tickets.
* Remove the winning ticket from the list, decreasing the total ticket count by 1.

#### Subsequent Winner Selections

For each subsequent winner `i` (starting from the second winner):

1. Use the **ticket\_id** of the previous winner's address.
2. Declare **ticket\_id** is  `s_i`.
3. Calculate the index of the winning ticket as `index_i = s_i mod (n - (i-1))`, where `n - (i-1)` reflects the updated total number of tickets after removing winners.
4. Remove the winning ticket from the list, continuing to adjust the total ticket count for each selection.

#### Repeat the Process

* Continue the process, using the **ticket\_id** of the most recent winner's address to select the next winner.
* Repeat until all desired tickets are picked or no tickets remain.\


####

#### EXAMPLE:

* Let's say the **Root Block** will be 838769 Its blockhash will be:  \
  [https://mempool.space/block/000000000000000000001b95867e0182e85e74313cf5b6b1080fe762634b70dd](https://mempool.space/block/000000000000000000001b95867e0182e85e74313cf5b6b1080fe762634b70dd)
* Total valid tickets: **888**\
  \
  **Select first winner:**
* Extract the last 9 characters of the hash code: `2634b70dd`
* Convert `634b70dd` to a decimal number: **10255823069**
* Perform the operation: **10255823069 mod 888** = **269**
* Therefore, address with index **269** is the first selected => **ticket\_id:** **7146**
* Next index selected will be **7146 mod 888** =  42 => **ticket\_id : 79040**
* **......**\


ticket\_id **79040** will serve as the basis (or 'seed') for determining the next winner\
This procedure will be repeated, using each new winner's wallet address as the seed for the subsequent selection, until a total of 333 winners have been chosen.

