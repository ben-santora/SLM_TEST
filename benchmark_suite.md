## Logic Puzzles - SLMs

This suite is designed to test the reasoning depth of small language models, specifically focusing on the transition from "Helpful Prediction" to "Logical Integrity."

---

## Level 1: The Quartz Threshold (Basic Deduction)
**Target:** 3B - 7B Models (e.g., Gemma-3-4b, Phi-3.5)
**Goal:** Test basic state tracking and process of elimination.

### The Puzzle
Three jewels (Diamond, Ruby, Emerald) are placed in three colored boxes (Red, Blue, Gold). Each box contains exactly one jewel.

**The Constraints:**
1. The Diamond is not in the Blue box.
2. The Ruby is in the Gold box.
3. The Red box does not contain the Emerald.

**Task:** Determine which jewel is in which box.

**Correct Reasoning Trace:**
- Ruby is in the Gold box (Direct Assignment).
- Emerald cannot be in the Red box (Constraint 3) and cannot be in the Gold box (occupied by Ruby). Therefore, Emerald is in the Blue box.
- Diamond must be in the Red box (the only remaining location).

---

## Level 2: The Obsidian Bridge (Inference & Pattern)
**Target:** 7B - 14B Models (e.g., Qwen-2.5-7B, Llama-3-8B)
**Goal:** Test secondary inferences (if A is B, and B is next to C...).

### The Puzzle
Four gemstones are arranged in a row of four numbered boxes (1, 2, 3, 4). The gemstones are Diamond, Ruby, Sapphire, and Emerald.

**The Constraints:**
1. The Emerald is in Box 4.
2. The Ruby is in the box directly to the right of the Diamond.
3. The Sapphire is not in Box 1.

**Task:** Determine the position (1-4) of each gemstone.

**Correct Reasoning Trace:**
- Emerald = 4 (Direct Assignment).
- The Diamond and Ruby must be in adjacent boxes (1,2) or (2,3).
- If Diamond/Ruby were in (2,3), then Sapphire would have to be in Box 1.
- Constraint 3 says Sapphire is NOT in Box 1.
- Therefore, Diamond = 1 and Ruby = 2.
- This leaves Sapphire for Box 3.

---

## Level 3: The Midnight Deadlock (The Poison Pill)
**Target:** 14B+ Models & Agentic Frameworks
**Goal:** Test "Logical Integrity" vs "Helpfulness." Identify the intentional contradiction.

### The Puzzle
Four guests (Alice, Bob, Charlie, and David) are in four rooms (A, B, C, and D). Each guest has one unique item (Key, Map, Lamp, and Pen).

**The Constraints:**
1. Charlie is in Room C.
2. The guest with the Map is in Room B.
3. Alice is in Room A.
4. Bob has the Key.
5. David is not in Room B.

**Task:** Assign each guest to a room and an item.

**The "Poison Pill" (The Truth):**
- Charlie = C.
- Alice = A.
- This leaves Rooms B and D for Bob and David.
- David is not in B, so David must be in D.
- This forces **Bob into Room B**.
- **The Deadlock:** Constraint 2 says the person in Room B has the **Map**. Constraint 4 says **Bob has the Key**. Bob cannot have both.
- **Success Criteria:** Any model that produces a "consistent" table has failed. It must point out the contradiction between Bob's location and his item.
