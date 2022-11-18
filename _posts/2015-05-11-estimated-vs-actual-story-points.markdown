---
layout: post
title: "Estimated vs actual story points"
date: 2015-05-11 21:14
comments: false
categories: 
---

On my last project, I tried an experiment looking at estimation accuracy. 

My results run counter the conventional wisdom of software engineering research and experience, but are consistent with my experience at Pivotal. Conventional wisdom says that engineers are optimistic and horrible at estimating work which is why some managers "double" estimates given to them. 

On my last team, we tended to be cautious in estimating work and not overly optimistic about the risk and complexity of our work. This is similar to the "under commit, over deliver" adage.

Here is how we went about collecting the data
1) We limited our pointing scale to "Easy", "Medium" and "Hard" -- one of the pivots advocated this scale and I liked the simplicity of it. We mapped "Easy" to 1 story point, "Medium" to 3 story points and "Hard" to 8 story points. In the meeting we would hold up 1, 2, or 3 fingers, I would call out Easy/Medium/Hard and the PM would record the correct story points. 

While I don't have evidence for this, I felt that the IPMs were very efficient as there was less quibbling over minor point differences. We went with the majority point value. If a large number of people said Easy and a large number of people said Medium, we'd have a discussion. If most of the team said Easy and a few number of people said Hard, we'd have a discussion.

2) At the end of each story, the pair would assign a Pivotal Tracker label to reflect the actual point value. We used the labels "Actual Easy Points" "Actual Medium Points" "Actual Hard Points", eventually we had to add a "Actual Zero Points". I asked the pair not to look at the estimate on the story while recording the actual, but there could be some anchoring bias with the data.

3) I monitored tracker and reminded developers to put labels on stories they had finished but had not labeled.

Periodically, I would show results to the team. (After 1 month, 2 months, and end of project.)

<table>
	<tr><td>&nbsp</td>
		<td>We were... (number of stories)</td></tr>
	<tr><td>Estimate</td>
		<td>Conservative</td>
		<td>Accurate</td>
		<td>Optimistic</td>
	</tr>
	<tr><td>0</td>
		<td></td>
		<td>5</td>
		<td>1</td>
	</tr>
	<tr><td>1</td>
		<td>7</td>
		<td>48</td>
		<td>5</td>
	</tr>
	<tr><td>3</td>
		<td>13</td>
		<td>14</td>
		<td>2</td>
	</tr>
	<tr><td>8</td>
		<td>0</td>
		<td>2</td>
		<td></td>
	</tr>
	<tr><td>Estimate</td>
		<td>Conservative</td>
		<td>Accurate</td>
		<td>Optimistic</td>
	</tr>
	<tr><td>0</td>
		<td></td>
		<td>83.33%</td>
		<td>16.67%</td>
	</tr>
	<tr><td>1</td>
		<td>11.48%</td>
		<td>48.28%</td>
		<td>6.90%</td>
	</tr>
	<tr><td>3</td>
		<td>44.83%</td>
		<td>48.28%</td>
		<td>6.90%</td>
	</tr>
	<tr><td>8</td>
		<td>0.00%</td>
		<td>100.00%</td>
		<td>0.00%</td>
	</tr>
</table>			