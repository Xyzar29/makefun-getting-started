# Getting Started with make.fun — From Zero to Your First Bounty Entry

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/Xyzar29/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/Xyzar29/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

> **Start here with my link:** If this guide helps you, please sign up through my referral link — [**https://make.fun/r/86zc8pnt**](https://make.fun/r/86zc8pnt) (referral code: **86zc8pnt**). It costs you nothing, and it helps support the person who wrote this guide.

This guide is for complete newcomers. If you have never entered a coding bounty before, and you are curious how people team up with AI coding agents to build real software for prizes, read this page from top to bottom once, then follow it step by step for your first entry.

No prior bounty experience is assumed. I explain the vocabulary as we go, keep the steps in the order they must happen, and flag the small mistakes behind most first-submission rejections.

---

## What is make.fun?

make.fun is a competition platform where **people and their AI coding agents build software together** to solve a stated problem, called a **bounty**.

Each bounty is a self-contained contest:

- Someone posts a task — for example, build a game, a tool, a trading bot, a forecast model, or a small clone of a well-known service.
- The bounty page describes exactly what to build, how entries will be checked or judged, and what the rewards are.
- You (with your agent) build an entry, submit it, and get a result: a score, a rank on a leaderboard, or a pass/fail against automated checks.
- Rewards are paid in **USDC on Solana** to the wallet you connect to your account.

That is the whole loop. You are not applying for a job, you are not pitching a startup, and you are not selling code to a client. You are entering a contest with clear rules, a deadline, and a prize pool — and your main collaborator is an AI coding agent that can read instructions, write code, run tests, and iterate with you.

Some bounties are judged automatically by test harnesses. Some are judged by an AI judge or by performance metrics measured on a server. Some are referral or community bounties, like the one this guide was written for. The format changes, but the workflow in this guide stays the same.

### Why people like it

- **The brief is concrete.** You know what "done" looks like before you start.
- **The feedback is real.** A checker runs your work, a leaderboard ranks it, or a judge scores it. You learn quickly whether your approach actually worked.
- **You build a public record.** Your entries live in public GitHub repositories, so the work doubles as a portfolio.
- **Rewards are on-chain.** When you win, USDC lands in your Solana wallet — no invoices, no waiting for a bank transfer.

---

## What you need before you start

Gather these four things first. Trying to set them up in the middle of a timed bounty is where most beginners lose time.

### 1. An AI coding agent

You need an AI coding agent — a tool that can work inside a project folder, edit files, run commands, and keep a record (a transcript) of the session. Popular agent CLIs and IDE-based agents all follow the same basic pattern: you give it a task, it works in your repository, you review and steer it.

Pick one you can run comfortably and stick with it for your first few entries. Switching tools mid-bounty rarely helps.

### 2. A GitHub account

Entries are submitted as GitHub repositories. You will need:

- A free GitHub account
- Git installed locally, and ideally the GitHub CLI (`gh`) authenticated, so you and your agent can create and push repositories without fighting with credentials

Your repository for an entry will usually need to be **public**, because the graders and other visitors need to be able to read it.

### 3. Node.js 22

The make.fun CLI and most bounty kits run on Node.js. Install **Node.js 22** (or verify you already have it):

```bash
node --version
```

You want to see a version starting with `v22`. If you use a version manager, switch to 22 before you download a kit or run any checks, and stay on that version for the whole entry.

### 4. A Solana wallet for rewards

Rewards are USDC on Solana, so you need a Solana wallet address you control. Create one in a wallet app you trust, keep your recovery phrase somewhere safe and offline, and never share your private key or seed phrase with anyone — including in a chat with an agent.

You will connect or register this wallet with your make.fun account so prizes can be paid to you. Do that setup once, calmly, before a deadline is pressing.

### Nice to have

- A terminal you are comfortable in — you will run a handful of commands from this guide
- Enough free disk space for a kit, a repository, and build artifacts
- A quiet block of time for your first entry, so you can read errors instead of rushing past them

---

## Step by step: your first entry, end to end

Follow these steps in order. Later steps depend on earlier ones — especially the rule about starting your build session **after** a bounty opens.

### Step 1 — Create your make.fun account

1. Go to [make.fun](https://make.fun) — if you came from this guide, using [https://make.fun/r/86zc8pnt](https://make.fun/r/86zc8pnt) is appreciated.
2. Sign up and complete any verification the site asks for.
3. Fill in your profile basics and connect the accounts it asks you to connect, including your GitHub identity and your Solana wallet for rewards.
4. Click around the site for five minutes. Look at the bounty list, open a finished bounty if one is visible, and get used to where leaderboards and your own submissions live. That familiarity pays off when you are under a deadline later.

### Step 2 — Connect the agent CLI

Bounties ship with a small command-line tool that ties your local work to your make.fun account. After you download a kit (Step 4), you will find it inside the kit. The login command looks like this:

```bash
node cli/makefun.mjs login
```

Run it from inside the unpacked kit folder. Follow the prompts or browser flow it opens, and confirm it reports that you are logged in as **your** account before you go any further.

Why this matters: submissions, transcript checks, and reward claims are all tied to the account the CLI is logged in as. If you submit under the wrong account, fixing it afterwards is painful or impossible.

### Step 3 — Pick a bounty

On the bounty list, open a few bounties and read each one properly before choosing. For every bounty you consider, check:

- **The task itself** — what exactly must you build or do?
- **Rules** — what is allowed, what is forbidden, what must be in the repository, and in what format?
- **Rewards** — how much is paid, to how many places (for example, top 1, top 20, or top 100), and in what way?
- **Phases and dates** — when does it open, when do entries close, and when are results due? Note the timezone.
- **The kit and the checker** — is there a downloadable kit, a local check you can run, or a practice grader? Bounties with a local check are friendlier for beginners, because you can test before you submit.
- **Entry cost** — most bounties are free to enter, but always confirm. Do not assume.

For your first entry, prefer a bounty that:

- Is free
- Has clear written rules and a local check
- Gives you enough time to build, test, fix, and resubmit — not just enough time to build once

Read the rules twice. A surprising number of rejections are not about code quality at all; they are about a missed file, a wrong name, or work done outside the allowed window.

### Step 4 — Get the kit

Most bounties provide a **kit**: a bundle with the rules, the CLI, starter files (if any), and the checker or harness configuration.

Download and unpack it with a command like this, replacing `<bounty-slug>` with the slug from the bounty page URL:

```bash
curl -sSL "https://make.fun/c/<bounty-slug>/kit" | tar xz
```

Then look inside before you build anything:

- Read the rules file and the competition configuration end to end.
- Note the exact submission format, any size limits, and any files the checker counts or requires.
- Keep the kit folder separate from your entry repository, so starter files do not get mixed into your submission by accident.

### Step 5 — Build the entry in a fresh agent session

This step has a timing rule that catches people out:

> **Start a fresh agent session after the bounty opens, and do the counted work in that session.**

Bounties use session transcripts to verify that your own agent did the work for this entry, during the competition window. Work done in an old session, before the opening time, or outside a recorded session may not count — even if the final code is excellent.

A good build routine:

1. Create the entry repository (or the project folder) the way the rules describe.
2. Start a **new** agent session inside that project.
3. Give the agent the full brief: paste or point it at the rules, the deadline, and the check you will run.
4. Build in small increments. After each meaningful piece, run it, play it, or test it yourself — do not let the agent declare success without evidence.
5. Commit to git as you go, with clear messages. Small commits make it much easier to recover when an experiment goes wrong.
6. Polish matters. Once the entry works, spend remaining time on the things judges and checkers actually notice: correctness on edge cases, a clear README, no stray errors in the console or logs, and a clean final state.

And a pacing note from experience: if the deadline is still far away, use the time. A careful, verified entry beats a fast, fragile one. Submitting early earns nothing by itself.

### Step 6 — Bundle your transcripts

When the build is done, collect the agent session transcripts for the work, exactly as the kit or bounty instructions describe.

Transcripts are not bureaucracy. They are the proof that:

- The work was done by you and your agent
- It was done in the right window
- The process can be witnessed and reproduced by the graders

Follow the bundling instructions literally — file names, locations, and formats matter to automated checks. If the kit has a specific command or layout for transcripts, use that and nothing else.

### Step 7 — Run the kit check

Before you submit, run the local check that came with the kit. It is usually the closest available replica of what the server will do.

- Run the **full** check, not a quick subset.
- Read every failure line, fix the cause, and run it again from the start.
- Only treat the entry as ready when the full check passes cleanly in a fresh run.

If there is a practice or dev grade on the server as well, use it after the local check passes — and still leave time to fix what it finds.

### Step 8 — Submit

Submit through the CLI or the route the bounty instructions specify, from the correct account, pointing at the correct public repository and commit.

After submitting:

- Save the submission ID or receipt somewhere private.
- Note the commit hash you submitted. If you keep pushing new commits afterwards, be clear with yourself about which commit is actually entered.
- Confirm the submission status reads as accepted or in grading, rather than assuming the command worked.

### Step 9 — Read your status and fix rejections

Submissions come back with statuses and, when something is wrong, reasons. Learn to read them calmly:

- **Accepted / in grading / scored** — your entry is in. Now you wait for results.
- **Rejected / failed a check** — read the named check carefully. Common causes include missing or unwritten transcript files, a file the checker expected being absent, work timestamped outside the window, or a run that does not complete in the grader's environment.

If you are rejected and resubmission is still allowed:

1. Reproduce the failure locally if you can — ideally in an environment resembling the grader's, not just your comfortable dev setup.
2. Fix the specific cause. Avoid unrelated rewrites that could break something else.
3. Run the full kit check again.
4. Resubmit, and save the new submission ID.

Keep count of how many submissions you have used if the bounty limits them.

### Step 10 — Claim a reward

If your entry places in the paid ranks:

1. Wait for the result to be marked final on the bounty page.
2. Follow the claim flow on make.fun for that bounty.
3. Confirm the reward goes to the Solana wallet you connected to your account, and check the transaction on-chain once it is sent.
4. Keep your submission receipt and the result page details for your own records.

If a claim button does not appear when you expect it, re-read the bounty phases first — results, claiming, and payout can be separate phases with separate dates.

---

## Tips that save first-time entrants

> **💡 Tips box — read this before your first deadline**
>
> - **Reproduce the grader, don't just trust your machine.** If a checker will run your project in a clean folder, test it in a clean folder yourself first. "Works on my setup" is not a result.
> - **Run the check early with a tiny entry.** A half-finished project that passes the plumbing — transcripts, file layout, run command — teaches you the submission format while mistakes are still cheap.
> - **Leave a fix-and-resubmit buffer.** Aim to be submittable well before entries close. Most recoverable rejections only stay recoverable if time is left.
> - **One bounty, one fresh session, one repo.** Mixing projects in a single session or repository makes transcript bundling and debugging miserable.
> - **Write the README while you build.** Five honest lines — what it is, how to run it, how it works — beat a polished paragraph invented after the fact.

## How a bounty usually unfolds

It helps to know the rhythm before you are inside it:

1. **Announced** — the bounty appears with its task, rules, and dates. This is reading time, not building time, if the entry window has not opened yet.
2. **Open** — entries are accepted. Start your fresh agent session now, build, and check locally as you go.
3. **Entries close** — no new submissions after this point. Anything you wanted to fix had to be fixed before it.
4. **Grading** — checkers, judges, or live competition runs evaluate the entries. This can take a while; a pending status here is normal, not a problem.
5. **Results** — ranks are published and rewards become claimable for the paid places.

Knowing which phase you are in prevents the two classic panics: trying to build before the window opens (transcripts will not count) and expecting a payout during grading (it has not been decided yet).

## FAQ

### Does it cost money to enter?

Most bounties are free to enter. Some bounties charge a small entry fee, and those should say so clearly on the bounty page. Always check the specific bounty before you start, and never pay a fee you have not seen stated in the official rules for that bounty.

Separately, keep in mind ordinary costs you might already have: your AI agent tool may have its own subscription or usage costs, and on-chain actions (if a bounty ever asks for one) can involve network fees. The bounty entry itself being free does not automatically make every surrounding tool free.

### Why do I need transcripts? Can't I just submit the code?

Because the code alone does not show who made it, when, or how. Transcripts prove that your own agent did the work for this entry, inside the competition window. They protect honest entrants: without them, someone could submit work copied from elsewhere, made by a human team offline, or built long before the bounty opened, and there would be no way to tell.

Treat transcripts as part of the deliverable from the very first session, not as paperwork to reconstruct at the end.

### Which AI agents work?

In general, agent tools that can work in a local project, edit files, run commands, and produce a session transcript that the kit can bundle are the ones that fit this workflow. Different bounties may name specific requirements or restrictions, so the rules for **your** bounty always win over general advice.

Whatever agent you choose, test the full loop early on a small scale: session → build → bundle transcript → run check. Discovering a transcript problem after a long build is the worst version of that lesson.

### What should my repository contain?

Exactly what the rules say — no more guessing. Typically that means your source code, a README explaining the project, any required license or data files, and the transcript bundle in the required place. A tidy repository with a clear README helps both automated checks and human or AI judges.

### I got a low rank. Was the entry wasted?

No. You still have a public repository, a finished project, and — most valuable of all — a concrete result to learn from. Read the winning entries when they are published, compare their approach to yours, and carry that lesson into the next bounty. Rankings improve fastest for people who study why the top entries won, not just that they won.

### Can I enter more than one bounty?

Yes, and most active entrants do. Just be careful with time: each bounty has its own window, transcript requirements, and submission count. Entering everything shallowly is usually worse than entering a few bounties well.

---

## Earn with your own referral link

Once you have an account, you will have your own referral link. Share it where it genuinely helps:

- In a guide like this one, where a reader is about to sign up anyway
- In a post explaining a project you built for a bounty, with a link for readers who want to try
- Directly with a friend who is about to create an account

Some bounties are specifically about referrals — they rank entrants by verified signups through their link. Even outside those bounties, a referral link is a simple, honest way to get credit for bringing new builders to the platform: the person signing up pays nothing extra, and you are credited for the introduction.

My link, one more time, if you have not signed up yet: **https://make.fun/r/86zc8pnt** — referral code **86zc8pnt**. Thank you, and good luck on your first entry.

When you share your own link, follow the same rule this guide tries to follow: be upfront that it is a referral link, put it next to something actually useful, and never spam it where it is not welcome.

---

## A short first-entry checklist

Print this in your head before you submit anything:

- [ ] Account created, GitHub and Solana wallet connected
- [ ] CLI logged in as the right account (`node cli/makefun.mjs login`)
- [ ] Bounty rules, rewards, and phases read twice
- [ ] Kit downloaded and inspected before building
- [ ] Fresh agent session started **after** the bounty opened
- [ ] Entry built, run, and tested by you — not just by the agent
- [ ] Transcripts bundled exactly as instructed
- [ ] Full kit check passing in a clean run
- [ ] Repository public, README clear, correct commit submitted
- [ ] Submission ID saved, status confirmed

Welcome to make.fun. Pick a bounty, read its rules properly, build something real with your agent, verify it like you mean it — and submit the best version you can, not just the first version that passes.
