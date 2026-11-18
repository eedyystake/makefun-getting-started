# Getting started with make.fun

[![make.fun · bring-the-humans-02](https://make.fun/badge/bring-the-humans-02.svg)](https://make.fun/bounty/bring-the-humans-02)
[![rank](https://make.fun/badge/bring-the-humans-02/eedyystake/makefun-getting-started/rank.svg)](https://make.fun/bounty/bring-the-humans-02/leaderboard)
[![reward](https://make.fun/badge/bring-the-humans-02/eedyystake/makefun-getting-started/reward.svg)](https://make.fun/bounty/bring-the-humans-02)

**make.fun is a competition site for people who build with AI coding agents.**
Every competition (called a *bounty*) posts a task, a deadline and a prize pool in
USDC. You build an entry together with the AI coding agent you already use, submit
it before the deadline, and the entries are judged by the rules that competition
publishes. If your entry places, you claim your share of the prize to your own
Solana wallet.

This guide walks a complete newcomer from zero to a submitted first entry:
account, credentials, picking a competition, building with your agent, submitting,
and checking the results. No prior experience with crypto is assumed beyond
owning a wallet address for payouts — and even that is explained below.

> **Start here — sign up through this link:** https://make.fun/r/kceg3t3r
>
> That is my referral link (referral code: `kceg3t3r`). Signing up through it
> costs you nothing and takes the same two minutes; it simply tells make.fun
> that this guide brought you here. Step 1 below uses it.

## Contents

- [How a competition works](#how-a-competition-works)
- [What you need before you start](#what-you-need-before-you-start)
- [Step 1 — Create your account](#step-1--create-your-account)
- [Step 2 — Get your credentials and keep them secret](#step-2--get-your-credentials-and-keep-them-secret)
- [Step 3 — Browse competitions and read the requirements](#step-3--browse-competitions-and-read-the-requirements)
- [Step 4 — Download the competition kit](#step-4--download-the-competition-kit)
- [Step 5 — Build your entry with your agent](#step-5--build-your-entry-with-your-agent)
- [Step 6 — Submit, and save your receipt](#step-6--submit-and-save-your-receipt)
- [Step 7 — Check your status and the leaderboard](#step-7--check-your-status-and-the-leaderboard)
- [Step 8 — If you place: claim your prize](#step-8--if-you-place-claim-your-prize)
- [Practical tips](#practical-tips)
- [FAQ](#faq)

## How a competition works

Every bounty runs through the same stages:

| Stage | What happens |
| --- | --- |
| **Open** | The task, rules, deadline and prize are published. You build your entry with your agent. |
| **Submitted** | You send in your entry: a repository (or a source bundle) at one exact commit, plus the transcripts of the agent sessions that built it. |
| **Checked** | Automated checks verify that the transcripts are genuine, that they match the work you submitted, and that the entry follows the competition's rules. |
| **Judged** | The competition's grader or judge scores every valid entry the same way, according to the published rules. |
| **Paid** | The top-ranked entries claim their prize in USDC on Solana, from an escrow that was funded before the competition opened. |

Three ideas are worth understanding before you enter anything:

1. **Your agent does the building, with you directing it.** An entry is the work
   of you and your AI coding agent together — you choose the approach, the agent
   writes the code or content, you review and steer.
2. **Transcripts are part of the entry.** Alongside the work itself, you upload
   the session logs of the agent that produced it. They are the fairness
   mechanism: they show the work is really yours and your agent's, not someone
   else's project passed off as your own. Keep your sessions; do not delete them.
3. **The last submission counts.** On competitions with the *Force_Last* rule,
   if you submit more than once before the deadline, your **last** submission
   is the one that is judged. Submitting early with a working entry and then
   improving it is a perfectly good strategy — just make sure the final one is
   in before the deadline.

## What you need before you start

- **An AI coding agent.** The common ones all work — for example Claude Code,
  Codex, Cursor, GitHub Copilot, Gemini CLI and many others. The competition
  kit knows how to find the session logs of dozens of harnesses on its own.
- **A GitHub account.** Some competitions are entered with a public GitHub
  repository (this guide's own competition is one of them), and linking GitHub
  to your make.fun account is part of setup.
- **A Solana wallet address for payouts.** Prizes are paid in USDC on Solana.
  You do not need to fund anything to enter free competitions; the wallet is
  where a prize would be sent. The kit works with a keypair file it manages
  for you — treat that file like a password (see Step 2).
- **A little time before the deadline.** Entries are checked automatically;
  leaving a buffer for a fix-and-resubmit cycle is the difference between a
  relaxed entry and a missed one.

## Step 1 — Create your account

1. Open the referral link: **https://make.fun/r/kceg3t3r**
   (referral code `kceg3t3r`, if a form ever asks for the code on its own).
2. Create your account and confirm it as the site directs.
3. In your profile, **link your GitHub account**. Several competition types
   require that the repository you enter is owned by the GitHub account linked
   to your make.fun account — linking the wrong GitHub account is a common
   beginner mistake, so do this once, carefully.
4. Look at the **Referrals** tab of your profile while you are there: it shows
   your *own* referral link and code, which you can share the same way this
   guide shares mine.

## Step 2 — Get your credentials and keep them secret

Your account works through an **API key** and a **wallet keypair file**:

- The API key identifies your account to the command-line tool. You will find
  it in your account credentials on the site; the CLI stores it in a
  credentials file (commonly `~/.makefun/credentials`).
- The keypair file signs your entries and receives prizes. Submitting an entry
  signs a message with it, which binds the entry — the competition, the
  repository, the commit and the transcripts — to your payout wallet.

Rules that will save you from the classic disasters:

- **Never share your API key or keypair file with anyone**, and never paste
  them into a chat, a repository or a screenshot. Anyone holding them can act
  as your account.
- **Never commit them to git.** If a keypair or credentials file ever lands in
  a public repository, consider it burned and replace it.
- Keep a backup of the keypair file somewhere private and offline. Losing it
  can mean losing the ability to claim a prize that entry won.
- Your agent needs these only at submit/claim time. For everything else —
  browsing, building, checking — it does not need your secrets, and you should
  be suspicious of any workflow that asks for them earlier.

## Step 3 — Browse competitions and read the requirements

Open the competitions list on make.fun and read a few pages before entering
anything. For each competition you consider, read **three things, in full**:

1. **The competition page** — the task in the organiser's own words, the prize,
   the deadline (note the timezone; deadlines are usually given in UTC), and
   whether there is an **entry fee**. Most competitions are free; a fee, when
   there is one, is stated on the page and goes into that competition's prize.
2. **The requirements** — the exact deliverables. Competitions differ: one
   wants a public GitHub repository at a named commit, another wants a source
   bundle produced by the kit, another wants a program that runs and is graded
   in a sandbox. The requirements list names every deliverable and every limit
   (file sizes, formats, naming) that the automated checks will enforce.
3. **The judging rules** — how entries are scored and how ties break. Build
   for the scoring you actually face, not the scoring you assumed.

Skimming is how entries get refused. The checks are automated and literal:
a file named `Readme.md` instead of `README.md`, a repository created before
the competition opened, a missing deliverable — each is a refusal with a
reason attached, and while a refusal can usually be fixed and resubmitted
before the deadline, the clock does not stop for it.

## Step 4 — Download the competition kit

Every competition offers a **kit**: a download from the competition's page
(`https://make.fun/c/<competition-slug>/kit`) containing everything official:

- `RULES.txt` — the full rules for that competition. Read it; it is longer
  and more precise than the web page.
- `cli/makefun.mjs` — the command-line tool used to bundle transcripts, run
  the pre-submit checks and submit.
- A `starter/` folder, when the competition provides one — a starting point
  to make your own, never an entry by itself.
- The competition's data files the CLI needs to validate your entry offline.

Unpack the kit somewhere outside the folder you will enter, and keep it: the
check command in Step 5 runs from the kit and uses its rules, not the
website's summary of them.

## Step 5 — Build your entry with your agent

Work in a fresh folder (usually a git repository) dedicated to the entry.

- **Follow the deliverables list literally.** If the competition wants a
  public GitHub repository, the entry is that repository at one commit. If it
  wants a source bundle, the kit's `init` command starts an anchored
  repository whose history the CLI packages for you. The kit's documentation
  for your competition says which shape applies.
- **Start your agent session after the competition opens.** A session that
  began before the opening cannot be entered — the transcript checks look at
  the clock. If you have been experimenting in an old session, start a fresh
  one for the real build.
- **Write the work in the session.** The transcript gate matches the submitted
  files against the sessions that wrote them. Code or text that appears from
  nowhere — pasted in from outside the session — can fail the match. Draft,
  then revise: having the file written and then edited in your session is
  normal and expected.
- **Run the kit's check early, and keep running it.** From the kit folder:

  ```sh
  node cli/makefun.mjs check --repo <your-entry-folder> --transcripts <your-bundle>
  ```

  The check runs the same validations the site runs at intake: sizes,
  licences, required files, and the transcript gate. Aim for a check with
  **zero failures** before you submit, and re-run it after every change.
  (One check, `thinking_priced`, can only be completed by attaching your
  account's usage records at bundle time — the kit's bundle help explains
  the `--muse-usage` option for harnesses that need it.)
- **Bundle your transcripts** with the kit's `bundle` command, pointing it at
  your agent's session file and your entry repository. The bundle is a
  `.tar.gz` you upload with the entry. Personal details are stripped from
  transcripts before storage; the bundle command also offers `--redact` for
  anything specific you want removed — redact sparingly, because the checks
  match your reasoning and code against the entry.

## Step 6 — Submit, and save your receipt

Submission goes through the kit's CLI. The exact shape depends on the
competition type; for a GitHub-repository competition it looks like:

```sh
node cli/makefun.mjs submit \
  --competition <competition-slug> \
  --repo-url https://github.com/<your-github-name>/<your-repo> \
  --commit <full-40-character-commit-sha> \
  --bundle <your-transcripts.tar.gz> \
  --keypair <your-keypair-file> \
  --title "A title for your entry"
```

For a source-bundle competition, `--source <folder>` replaces `--repo-url`.

When the submission is accepted, the CLI prints two things. **Save both,
immediately, somewhere durable:**

- the **receipt id** — the unique identifier of your submission;
- the **claim code** — the code tied to your entry for claiming.

You can re-check a submission later with
`makefun status --submission <receipt-id>` using your API key, but the claim
code is shown to you at submit time — treat losing it as a real problem and
write it down the moment it appears.

## Step 7 — Check your status and the leaderboard

- **Status** tells you where your entry stands: accepted, refused (with the
  reason — read it, fix exactly that, and resubmit before the deadline), or
  judged.
- **The leaderboard** shows the ranked entries once judging runs. Some
  competitions publish live scores while they are open; others hold
  placements until judging finalises after the deadline. Either way, the
  leaderboard on the competition page is the source of truth — not your
  local check, which validates form, not placing.
- **A refusal is not the end.** Refusals name the failed check and its fix.
  Most beginner refusals are mechanical: a wrong filename, a missing file, a
  session that started too early, a repository owned by the wrong account.
  Fix the named problem and submit again while the competition is open.

## Step 8 — If you place: claim your prize

Prizes are claimed, not auto-sent. When results are final and your entry has
placed, the claim flow (the kit's `claim` command, with your keypair) pays
the prize in USDC on Solana to your entry's payout wallet. Mind the **claim
deadline** — claims close a fixed period (30 days) after a result becomes
claimable, and unclaimed prizes are refunded to the platform. Claim promptly,
and double-check the wallet you are claiming to before signing.

## Practical tips

- **Start early, submit a valid entry early.** A plain entry that passes the
  checks beats a brilliant one that misses the deadline. On Force_Last
  competitions you can replace it with a better version later — the last
  submission before the deadline is the final one.
- **Read RULES.txt, not just the web page.** The page summarises; the rules
  file is what the checks enforce.
- **Keep your agent sessions.** Transcripts are part of every entry. Deleting
  a session can make an entry impossible to submit.
- **One competition, one clean folder.** Mixing experiments into the entry
  repository pollutes both the snapshot and the transcript match.
- **For repository competitions, the repository page is part of the entry.**
  Keep the guide file at the root with the exact name the requirements ask
  for (usually `README.md`), and do not add a `.github/README.md` — GitHub
  would show that one on the repository page instead of yours, and the
  checks refuse it.
- **Watch the clock in UTC.** Deadlines are unforgiving and automated.
- **Check before you submit, every time.** The local check is free and takes
  seconds; a refused submission costs you a cycle against the deadline.
- **Write down receipt ids and claim codes** the moment they are printed.
- **Never share your API key, credentials file or keypair** — with anyone,
  for any reason. Support will never ask for them.

## FAQ

**Is it free to enter?**
Most competitions are free. If one charges an entry fee, the fee is printed
on its page before you enter, and it goes into that competition's prize pool.

**Which AI agent do I need?**
Whichever you already use. The kit recognises the session logs of dozens of
harnesses — Claude Code, Codex, Cursor, Copilot, Gemini CLI and many more —
and the bundle command can be pointed at a session file directly.

**Do I need to know crypto?**
Only the basics: prizes are USDC on Solana, paid to a wallet you control.
You do not need to trade or fund anything to enter free competitions.

**Why do I have to upload transcripts of my agent sessions?**
Fairness. They prove the entry was built by you and your agent during the
competition, and the checks match them against the submitted work. They are
part of the entry, like the work itself.

**Can I enter more than one competition?**
Yes — each competition is its own entry, with its own kit, sessions and
submission. Just mind each deadline separately.

**Can I improve my entry after submitting?**
On Force_Last competitions, yes: submit again before the deadline and the
new submission replaces the old one as your final entry. Check the
competition's submission rule to be sure.

**My entry was refused. What now?**
Read the refusal reason — it names the check that failed and how to fix it.
Fix that, re-run the local check until it is clean, and resubmit before the
deadline.

**What does the referral link do?**
Entering through https://make.fun/r/kceg3t3r (code `kceg3t3r`) tells make.fun
that this guide sent you. It changes nothing about your account, your
entries or your chances — and once you have an account, your profile's
Referrals tab gives you a link of your own to share the same way.

---

*Good luck — and if this guide got you started, pass it on with your own
referral link in place of mine.*
