---
layout: essay
type: essay
title: "Reflect on Software Engineering"
# All dates must be YYYY-MM-DD format!
date: 2025-05-10
published: true
labels:
  - Software Engineering
  - Learning
---

<img width="500px" class="rounded float-start pe-4" src="../img/software_engineering.jpg"><br><br><br><br><br><br><br><br><br><br><br>

<h4>Introduction</h4>
<p>
What should we be mindful of when developing software as a team? Compared to self-development, team-development enables a much faster process due to a greater pool of ideas and the division of tasks. However, working in a team also introduces potential pitfalls stemming from insufficient coordination. In this essay, I will reflect on key considerations for successful team development, focusing on the following two topics:
  <li>Open Source Software Development</li>
  <li>Coding Standard</li>
</p>

<h4>Open Source Software Development</h4>
<h6>【What is Open Source Software Development?】</h6>
<p>
The first concern is miscommunication in open-source development. Open source development refers to making source code publicly accessible, enabling team members to share their work by sequentially updating and publishing code.
</p>

<h6>【The Problem and Our Experience】</h6>
<p>
Developers often base their work on previously written code. But what happens when the reference code has been updated? If the foundational system changes, the newly written code may no longer function correctly. To address this, we managed our repository on per task and clearly communicated all changes at Discord. In open-source software development, it's crucial to clarify the order of updates by task and ensure that all team members have at least a general understanding of the overall system.
</p>

<h4>Coding Standards</h4>
<h6>【What are Coding Standards?】</h6>
<p>
The second issue is miscommunication caused by inconsistent coding standards. Coding standards refer not just to the minimal syntax required for code to function, but to a set of rules designed to make the code visually and structurally understandable. These rules include indentation, formatting, and overall structure, requiring developers to pay attention to more than wheather the code correctly works.
</p>

<h6>【The Problem and Our Experience】</h6>
<p>
When coding conventions differ, even functionally identical code can appear completely different. Our team used ESLint to maintain consistent syntax formatting, but because we hadn’t aligned on the ordering of functions, how to split files, or how to use APIs, it took time to understand the purpose and interconnection of each file. Since every developer needs to grasp the overall architecture to some degree, a shared understanding of code structure is also necessary.
</p>

<h4>Conclusion</h4>
<p>
Through my first experience with team development, I came to appreciate its efficiency. Development done alone can be accelerated significantly when done as a team. However, in open-source software development, coordination is essential. Moving forward, I hope to consciously share ideas and understanding within a team, while continuing to grow as a software engineer.
</p>
