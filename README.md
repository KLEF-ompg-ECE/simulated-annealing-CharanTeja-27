# Assignment 1 — Simulated Annealing: Exam Timetable Scheduling
## Observation Report

**Student Name  :** BENNURI CHARAN TEJA
**Student ID    :** 2310040035
**Date Submitted:** 17-03-26 

---

## How to Submit

1. Run each experiment following the instructions below
2. Fill in every answer box — do not leave placeholders
3. Make sure the `plots/` folder contains all required images
4. Commit this README and the `plots/` folder to your GitHub repo

---

## Before You Begin — Read the Code

Open `sa_timetable.py` and read through it. Then answer these questions.

**Q1. What does `count_clashes()` measure? What value means a perfect timetable?**

```
count_clashes() counts how many exam conflicts are in the timetable (like students having two exams at the same time). A perfect timetable has 0 clashes, meaning no conflicts at all.
```

**Q2. What does `generate_neighbor()` do? How is the new timetable different from the current one?**

```
generate_neighbor() makes a small change to the current timetable (like moving one exam to a different slot). The new timetable is slightly different so the algorithm can explore new possibilities.
```

**Q3. In `run_sa()`, there is this line:**
```python
if delta < 0 or random.random() < math.exp(-delta / T):
```
**What does this line decide? Why does SA sometimes accept a worse solution?**

```
This line decides whether to accept the new solution. If the new one is better, it always accepts it. If it is worse, it may still accept it based on probability, so the algorithm can escape local minimums.
```

---

## Experiment 1 — Baseline Run

**Instructions:** Run the program without changing anything.
```bash
python sa_timetable.py
```

**Fill in this table:**

| Metric                               | Your result |
|--------------------------------------|-------------|
| Number of iterations completed       |    1379     |
| Clashes at iteration 1               |     12      |
| Final best clashes                   |     3       |
| Did SA reach 0 clashes? (Yes / No)   |     NO      |

**Copy the printed timetable output here:**
```

  Final Timetable
------------------------------------------
  Slot 1:  Geography
  Slot 2:  Chemistry, English
  Slot 3:  History, Computer Science, Economics
  Slot 4:  Biology, Statistics
  Slot 5:  Mathematics, Physics
------------------------------------------
```

**Look at `plots/experiment_1.png` and describe what you see (2–3 sentences).**  
*Where does the biggest drop in clashes happen? Does the curve flatten out?*
```
At the start, clashes drop quickly from 12 to around 6. After that, improvement becomes slow and the curve flattens. Near the end, there is a small improvement to 3 clashes.
```

---

## Experiment 2 — Effect of Cooling Rate

**Instructions:** In `sa_timetable.py`, find the `# EXPERIMENT 2` block in `__main__`.  
Copy it three times and run with `cooling_rate` = **0.80**, **0.95**, and **0.995**.  
Save plots as `experiment_2a.png`, `experiment_2b.png`, `experiment_2c.png`.

**Results table:**

| cooling_rate | Final clashes | Iterations completed | Reached 0 clashes? |
|-------------|--------------- |----------------------|--------------------|
| 0.80        |         8      |     31               |        NO          |
| 0.95        |          3     |     35               |       No           |
| 0.995       |         3      |    1379              |       NO           |

**Compare the three plots. What do you notice about how fast vs slow cooling affects the result? (3–4 sentences)**  
*Hint: Fast cooling = temperature drops quickly. Does it have time to explore well?*
```
With 0.80, cooling is very fast, so the algorithm stops early and gives a poor result. With 0.95, it does better because it explores more. With 0.995, cooling is slow, so it explores more deeply and gives the best and most stable result.
```
Which cooling_rate gave the best result? Why do you think that is?
```
This is because it cools down very slowly, so the algorithm has more time to explore different solutions. It can avoid getting stuck in bad local solutions and gradually improve the timetable. Faster cooling rates stop too early, so they miss better solutions.
```

---

## Summary

Complete this table with your best result from each experiment:

| Experiment               | Key setting          | Final clashes | Main finding in one sentence |
|------------              |-------------         |---------------|------------------------------|
| 1 — Baseline             | cooling_rate = 0.995 | 3             | Slow cooling improves solution quality.|
| 2 — Cooling rate         | cooling_rate = 0.995 | 3             |Slower cooling gives better results |

In your own words — what is the most important thing you learned about Simulated Annealing from these experiments? (3–5 sentences)
```
Simulated Annealing works best when it balances exploration and improvement. I learned that cooling rate is very important — if it cools too fast, the algorithm gets stuck in a bad solution. Slower cooling gives it more time to explore and find better results. Also, accepting worse solutions sometimes helps it escape local minima. Overall, tuning parameters is key to getting a good timetable.
```

---

## Submission Checklist

- [ yes] Student name and ID filled in
- [ yes] Q1, Q2, Q3 answered
- [ yes] Experiment 1: table filled, timetable pasted, plot observation written
- [ yes] Experiment 2: results table filled (3 rows), observation and answer written
- [ yes] Summary table completed and reflection written
- [ yes] plots/ contains: experiment_1.png, experiment_2a.png, experiment_2b.png, experiment_2c.png