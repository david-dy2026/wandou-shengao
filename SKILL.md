---
name: wandou-shengao
description: Review a finished Chinese draft (short-video script, article, social post, course lesson, poster copy, slide talk) through four independent reader lenses before it is published - picky user, instructional designer, newcomer, and demanding problem-solver. Use when the user asks to review, critique, stress-test, or find problems in an existing draft, or says 四视角审稿 / 挑剔的用户 / 帮我挑毛病 / 这稿行不行. Do not use to write a new draft or to polish prose without offering critique.
---

# 豌豆四视角审稿

The job is to turn "这样行不行？" into "读者会在哪一句走，以及换成哪一句就不走了".

A writer looks forward: what I want to say, who I want to reach, what I want them to do. From that direction everything sounds fine. Reviewing means turning around: the draft already exists, so look at it with the eyes of the person receiving it, walking backward from the end.

From the front there is one view. From the back there are four. The difference is not effort, it is standpoint.

## When To Use

Use this skill when the user has an existing draft and wants it judged, not written:

- short-video scripts and spoken scripts
- WeChat Official Account articles, Xiaohongshu posts, Moments posts
- course lessons, tutorials, live-talk outlines
- poster copy, landing page copy, slide decks

Do not use it when there is no draft yet. If the user wants both, write the draft first, then run this skill as a separate pass - and say so explicitly, because the same model that wrote it will otherwise defend its own output.

## Step 0: Ask One Thing Only

Ask who the audience is, in one line: "想做自媒体但还没开始的上班族", "已经装好工具的学员", "朋友圈里的同行".

If the user gives no audience, assume "普通人、没背景、刷到这条内容的陌生人" and put that assumption in the first line of the verdict.

Ask nothing else. A review is not an interview.

## The Four Lenses

The lenses must not overlap. Overlapping lenses become one person saying "我觉得还行" four times.

| Lens | What he cares about | What he picks at | Why he must be there |
| --- | --- | --- | --- |
| **挑剔的用户** Picky user | Why should I believe you, why give you my time | Empty claims, stacked adjectives, conclusions without evidence, performed expertise | He is 80% of the real world and leaves within three seconds |
| **课程设计大师** Instructional designer | Is the structure right, can this actually be learned | Wrong order, missing prerequisite, telling without practicing, the hard part buried mid-way | Half of whether content works is structure, not wording |
| **对产品了解不深的用户** Newcomer | What does this have to do with me | Jargon, insider slang, assumed prior knowledge, metaphors nobody can picture | Newcomers are the majority; they leave instead of asking |
| **对解决问题非常较劲的用户** Demanding problem-solver | Which of my problems did you actually solve | Big promise, small delivery, dodging the real difficulty, beautiful but unusable | He is where conversion and word of mouth actually come from |

The four faces map to four losses, in the order they happen: **不信 → 学不会 → 看不懂 → 不服气**.

**挑剔的用户 is the default lead lens.** If there is only time for one pass, run him.

## How To Run

**One lens per pass. Four passes, then deliver once.** Do not report after each lens - the previous verdict drags the next one.

- If the environment has subagents, run four in parallel and state in each prompt: work independently, do not read the other three verdicts.
- If there are no subagents, run them one at a time. Before each pass, re-read the draft fresh, as if for the first time.
- If the same model wrote the draft, open with a one-line role reset: "我现在是没见过这段内容的另一个人." Then start.

## What Each Lens Must Return

Four slots. A comment missing any slot does not count:

```
1. Where I stop / leave / give up (quote the exact sentence)
2. Why (which word, which logic, which psychology - never "感觉不够吸引人")
3. Replace with (a full sentence the user can paste in, not a direction)
4. Evidence (which experience, which comparable case, what data)
```

Slots 1 and 3 carry the leverage. Without a quote, the model produces correct but useless generalities. Without replacement text, it says "建议更具体一点" and the user has to ask again.

## Merge Rules

| Situation | What to do |
| --- | --- |
| All four lenses raise it | Must fix, list first |
| Two lenses raise it | Fix if it damages trust (不信) first, otherwise by damage order |
| One lens only | Taste difference, list last, optional |
| Two lenses contradict | Do not decide for the user; put both fixes side by side with their cost |

Forty comments usually contain thirty that contradict each other. Fix the shared ones, leave the rest.

## Output Order

Follow this order. The first two are for use, the last two are for judgment.

**1. Verdict** - the single most damaging problem, in one sentence, no preamble.

**2. Must-fix list** - line by line: `原文` → `病在哪` → `换成这句`. Pasteable, no follow-up question needed.

**3. Revised full draft** - apply every must-fix item and hand back a complete usable version. Only touch what was flagged. Do not upgrade the tone, do not add rhetoric, do not delete the author's spoken phrasing.

**4. Optional** - one-line items, no elaboration.

## Hard Rules

1. **The reviewer cannot be the writer.** Even if it is the same model, change role, change lens, re-read from scratch.
2. **Evidence only, no feelings.** "这段不够打动人" is worthless. "第三句全是抽象名词，读者脑子里出不了画面" is usable. If a comment is the former, send it back.
3. **Only fix real problems.** See merge rules. Editing in all forty comments produces a draft that is the average face of four people.
4. **Stop after two or three rounds.** Returns collapse after round three; more is self-consumption. Ship with a little imperfection and read real feedback.

## Common Faults In Chinese Drafts

Check these by default; a hit is a must-fix, not a style preference. Details and examples in `references/review-checklists.md`.

- **替读者下结论.** "一条都反驳不了""我一直以为……其实……" Report what happened and how you reacted; leave the conclusion to the reader.
- **自我标榜的口号.** "我给自己定了个规矩""我的原则就是……" If readers did not notice it, announcing it reads as posturing. Carry the same meaning with a fact.
- **生造搭配、术语化比喻.** "提问这个动作在帮你排序" → "能把问题问出来，说明你自己已经想过一遍".
- **爹味说教、文艺腔.** "别急着花钱买课""心里有个坎儿过不去".
- **逻辑连接词堆叠.** In spoken scripts, hunt 因为/所以/但是/只是 and cut or split.
- **读不出来的英文.** Keep the term if it can be pronounced, follow it with a plain-language gloss; if it cannot be pronounced, replace it.
- **宏观趋势开头.** "现在 AI 发展这么快" is the author's view. Start from the reader's desire or pain.
- **一句话塞三层意思.** Split it, one layer per sentence.
- **同一个意思说了两遍.** Delete the later one.

## Common Misuse

- **Asking one model to play all four at once.** Every lens gets shallow. Batch them, or demand independence.
- **Letting it "make the draft better".** It will flatten the voice into a template. The only job is fixing what was flagged.
- **Applying all forty comments.** The draft becomes nobody's.
- **Reviewing an eighth time.** The meaning of round eight is zero.

## Reference Files

- `references/review-checklists.md` - per-lens follow-up questions, merge template, and two extra uses of the same move (reviewing an AI answer, reviewing your own decision).
- `references/test-steps.md` - how to try the skill and what a good result looks like.
