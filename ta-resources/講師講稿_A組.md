# Instructor Script — RL Lab, Group A (Rein Room Platform)

> **使用說明**
> `【動作】` = 你的行為提示，**不念出來**。
> 引號內是**口說英文講詞**，可照念或自由調整語氣。
> **粗體**是需要念慢、讓學生記住的關鍵詞。

---

## ══ Day 1 ══

---

### 🖥️ Slide 1 — Title (1 min)

【開 slides_A組.html，全螢幕投影。第 1 張：標題頁】
【站到講台正中，等學生安靜，環視一圈再開口】

"Hello everyone. My name is **Colombo Chao** — you can call me Colombo. I'm a graduate researcher at Yuan Ze University, and today I'll be your instructor for this two-day lab."

"This is also part of my research. Your work and observations are data for my thesis. So please take each task seriously — what you do here genuinely matters."

---

### 🖥️ Slide 2 — Course Overview (2 min)

【按 → 切到第 2 張：兩天課程結構】

"Two days, five tasks. The structure is on the screen."

"For each task: I'll play a short demo video, then you do it yourself on the platform. When you're done, raise your hand — the TA will come check your work."

"The platform you're using is called **Rein Room** — a browser-based game environment built for this course. No coding required. You'll adjust parameters, watch the agent learn in real time, and answer questions about what you observe."

"Questions go to the TA, or raise your hand for me. No question is a stupid one."

---

### 🖥️ Slide 3 — Poll (2 min)

【按 → 切到第 3 張：互動提問頁】

"Before we dive in — quick question."

"Have you ever studied reinforcement learning before? Raise your hand if yes."

【停，數一下舉手的人，點評】

"Okay. How about — heard of it, but never actually tried it?"

【停，數一下】

"And completely new to the topic?"

【停】

"Perfect. That's exactly the range I expected. Whether you've seen this before or not — today's format is hands-on, so everyone will be starting from the same place operationally."

---

### 🖥️ Slide 4 — What is RL? (2 min)

【按 → 切到第 4 張：Agent / Environment 圖】

"Here's the core idea — one picture, one sentence."

"There's an **agent** — the learner. There's an **environment** — the world it operates in. The agent takes an **action**, the environment responds with a new **state** and a **reward**. The agent uses that feedback to decide what to do next."

"That loop — action, feedback, adjust — repeated thousands of times, is how reinforcement learning works."

"Every task today is a version of this loop. You'll see it in action."

---

### 🖥️ Slide 5 — Repo + Environment Setup (3 min)

【按 → 切到第 5 張：QR code 頁】

"Alright — scan this QR code, or type the URL. This GitHub page is your guide for both days."

【等學生掃碼或打 URL，助教協助確認】

"Once you're on the page — click the Rein Room link and make sure the platform loads. You should see the game icons on the homepage."

【等 90 秒，確認全員就緒。有問題的讓助教處理。】
【關閉投影片，後續直接在 README 頁面上操作】

"Good. Keep that page open — you'll use it all day."

---

### 🎯 T1 · MAB — Multi-Armed Bandit (25 min)

#### Intro (2 min)

"The first task is called **Multi-Armed Bandit** — MAB for short."

"Imagine you walk into a casino. There are many slot machines, but you don't know which one pays out the most. How do you decide whether to keep playing the same machine, or try a different one? That tension — between **exploiting** what you already know and **exploring** what you don't — is one of the most fundamental problems in reinforcement learning."

#### 【播放影片】

【全螢幕播放 A1 影片：https://youtu.be/YClKpairwDo】

【影片結束後繼續說】

"The key parameter is **ε — epsilon**. On the platform you'll see a slider for it. ε = 0.9 means the agent explores 90% of the time. ε = 0.1 means it mostly sticks with what it thinks is best."

"**Task T1**: Run ε = 0.9 and ε = 0.1. Describe the difference in the reward curve. Which one learns better, and why?"

#### 【學生操作，走下講台巡視 18 min】

【找不到 ε 滑桿 → 提示：進入 MAB 遊戲後，右側參數面板】
【問要跑幾回合 → 說：At least 100 episodes — let the curve stabilize】
【完成的學生 → 追問：Which curve rises faster? What does that tell you about exploration?】

#### Wrap-up (3 min)

"Here's the takeaway: **exploration has a cost, but without exploration there's no learning**. High ε finds better options eventually, but wastes time trying bad ones. Low ε converges fast but might miss something better. Neither is always right — it depends on the problem."

"You'll see this trade-off in every task this week."

---

### 🎯 T2 · Maze 1D — Q-table & Bellman Update (25 min)

#### Intro (2 min)

"Next: a maze. The simplest possible one — a straight line. The agent moves left or right to find the goal."

"This time the agent doesn't just choose actions — it learns to **evaluate positions**. It builds a table of values: for every position, how good is it to be here? That's the **Q-table**."

"Every step produces three things: a **State**, an **Action**, and a **Reward** — S, A, R. You'll see them on the platform. Your job is to recognize them."

#### 【播放影片】

【播放 A2 影片：https://youtu.be/0t8htN7eXIo】

【影片結束後】

"**Task T2**: Find the S, A, R on the platform — point them out. Then explain in your own words what the **Bellman update** is doing: how did this step change the Q-value for that position?"

"No math required. Just explain the logic."

#### 【學生操作，巡視 18 min】

【看不懂 Q-value 數字 → 提示：Higher Q-value = the agent thinks that position is more worth being in. Cells closer to the goal have higher Q-values.】
【問 Bellman 怎麼說 → 提示：The value of this state = immediate reward + discounted best future value. Say that in your own words.】

#### Wrap-up (3 min)

"**The Bellman equation** is the engine of Q-learning. Every step nudges the Q-value a little closer to the truth. Run enough steps, and the table converges. Everything else in RL — including deep neural networks — is built on this idea."

---

### 🎯 T3 · Maze 2D — Policy Heatmap (30 min)

#### Intro (2 min)

"Now we go 2D. A grid maze — the agent can move up, down, left, right."

"Why is this harder? **The state space is much larger.** A 1D maze had maybe 20 positions. A 2D maze has hundreds of cells, each needing to be learned separately."

"After training, you'll see a **Policy Heatmap**: brighter color means the agent thinks that cell is more valuable. Arrows show the preferred direction at each cell."

#### 【播放影片】

【播放 A3 影片：https://youtu.be/6TSTonFAClA】

【影片結束後】

"**Task T3**: On the heatmap, trace the path from Start to Goal. Follow the bright cells and arrows. Then explain — why are certain cells brighter than others?"

#### 【學生操作，巡視 23 min】

【熱圖顏色都一樣 → 回合數不夠，繼續跑】
【進階 → 讓學生換 Walled In 難度，觀察路徑如何繞牆】

#### Wrap-up (2 min)

"The heatmap *is* the Q-table — just visualized. It lets you see inside the agent's head: where it thinks is worth going, and where it doesn't. That kind of interpretability is rare in machine learning. Enjoy it while it lasts."

---

### ☕ Break (10 min)

"Alright, that's the first half of Day 1. Take ten minutes — water, bathroom, stretch."

【離開講台，讓學生真正放鬆】

---

## ══ Day 2 ══

---

### 🟢 Opening (2 min)

"Welcome back. Yesterday you did three tasks — MAB, Maze 1D, Maze 2D. Today we step up: **continuous state spaces**."

"What does that mean? Yesterday's maze had discrete positions — a finite number of cells. Today's environments use **real-valued states**: position, velocity, angle — infinitely many possible values. How does the agent learn?"

"The answer is **discretization**: slice the continuous space into bins, then apply the Q-table you already know. But the finer the bins, the more the agent has to learn. You'll feel that trade-off directly today."

---

### 🎯 T4 · Heli — Reading Training Curves (30 min)

#### Intro (2 min)

"Task 4 is a helicopter game — fly horizontally, dodge obstacles. **Continuous state**: position, velocity, and so on."

"The main focus today isn't just running the agent — it's **reading the training curve**. That graph of reward over episodes: what is it telling you? Is the agent improving? Plateauing? Oscillating?"

#### 【播放影片】

【播放 A4 影片：https://youtu.be/BWvJVxiQ-hg】

【影片結束後】

"**Task T4**: Run at least 50 episodes. Then describe the reward curve trend — rising, flat, or noisy? Give your best explanation for why it looks that way."

"Rising = the agent is learning. Flat or noisy = it might need more time, or the parameters might need tuning."

#### 【學生操作，巡視 23 min】

【Rein Room 即時顯示飛行動畫和曲線，視覺直觀】
【曲線很亂 → 正常。Look at the smoothed moving average, not individual points.】
【鼓勵學生嘗試不同回合數，對比早期和晚期曲線差異】

#### Wrap-up (3 min)

"**The training curve is your diagnostic tool.** A flat curve doesn't mean failure — it might just need more episodes. A wild curve might mean the learning rate is too high. Reading these graphs is a skill, and you practiced it today."

---

### 🎯 T5 · Fighter — Optional Challenge (open-ended)

#### Intro (2 min)

"The last one: a fighter jet game. Shoot rocks, dodge them, survive. This is the hardest environment — **5-dimensional continuous state**, 4 actions, 5 difficulty modes."

"This task is **optional**. If you haven't finished T4, keep working on that. If T4 is done, come try this."

#### 【播放影片】

【播放 A5 影片：https://youtu.be/rhmJb94PZVU】

【影片結束後】

"No fixed requirement — **explore freely**. Try different difficulty modes on Rein Room. See how the agent's behavior changes as the challenge increases. If you notice something interesting, write it down."

#### 【學生自由探索 15 min，走動個別聊觀察】

---

### 🎤 Closing Discussion (10 min)

【不需要投影，站台前即可】

"Before we wrap up, a few questions. No right answers — just think out loud."

"**How was this different from what you imagined AI learning would look like?**"

【等 2-3 個學生回答，追問：Why did you expect that?】

"**Which task do you think was hardest for the agent — and why?**"

【引導：state space size / sparse rewards / exploration difficulty】

"Here's the bigger picture: everything you did this week — Q-table, Bellman updates, exploration vs exploitation — these are the same core ideas behind the systems you hear about in the news. Scale them up with deep neural networks, and you get the RLHF training that fine-tunes ChatGPT. You've touched the foundation."

"Thank you. The TA will collect the forms. Feel free to ask questions before you leave."

【下課】

---

## 📎 Video Links

| Task | Topic | Link |
|------|-------|------|
| A1 | MAB — Exploration vs Exploitation | https://youtu.be/YClKpairwDo |
| A2 | Maze 1D — SAR & Q-table | https://youtu.be/0t8htN7eXIo |
| A3 | Maze 2D — Policy Heatmap | https://youtu.be/6TSTonFAClA |
| A4 | Heli — Training Curves | https://youtu.be/BWvJVxiQ-hg |
| A5 | Fighter — Optional | https://youtu.be/rhmJb94PZVU |

---

## 📎 Rein Room Quick Reference

| Task | How to enter | Key action |
|------|-------------|------------|
| T1 MAB | Homepage → MAB | Adjust ε slider on right panel; press Run |
| T2 Maze 1D | Homepage → Maze 1D | Watch Q-value panel update on the left |
| T3 Maze 2D | Homepage → Maze 2D | Select Walled In; open Heatmap (bottom right) |
| T4 Heli | Homepage → Heli | Run 50+ episodes; read the curve on the right |
| T5 Fighter | Homepage → Fighter | Switch Mode 1–5; observe behavior changes |

---

## 📎 Troubleshooting

| Problem | Fix |
|---------|-----|
| Platform won't load | 重新整理；嘗試無痕視窗；確認網路連線 |
| Training is slow | 正常，Rein Room 是即時模擬，讓它跑，不要一直重開 |
| Can't see the curve | 確認已按 Start Training，不只是 Preview |
| Heatmap looks blank | 回合數不夠，繼續跑到至少 50 回合 |
| Student finishes way ahead | 請他試 T5 Fighter，或解釋給旁邊同學聽 |
| "What's the real-world use?" | "This is the same algorithm, scaled up with neural nets, that trains ChatGPT's RLHF layer." |
