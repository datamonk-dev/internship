# Git Reset — Rewind Time (Responsibly!)

Sometimes you commit too early. Sometimes the commit just isn’t right. And sometimes... it’s a total mess.

> *“I wish I could just undo that last commit…”*

Good news: **`git reset`** lets you rewind your Git history.

But heads up — not all resets are created equal. Some let you keep your work, others wipe it out completely.

Let’s walk through them with real examples from your project.

---

## Scenario: You Made 3 Commits

Let’s say you’ve made these three commits:

1.  `Add homepage`
2.  `Add about section`
3.  `Add weird font and broken layout` ← You want to undo this one

You want to get rid of the third commit and maybe fix it before anyone sees it. Here’s where `git reset` steps in.

---

## `git reset --soft` — Undo the Commit, Keep the Work

```bash
git reset --soft HEAD~1
```

> *"Oops! I shouldn’t have committed yet, but I still want the changes."*

### What it does:

* Removes the last commit
* Keeps your changes in the **staging area** (ready to recommit)

### Example Use Case:

You're trying out different fonts in your portfolio and accidentally committed your test code. You want to tweak it a bit more before committing again.

```bash
git reset --soft HEAD~1
# Edit your CSS or HTML
git commit -m "Add better font styles"
```

 Perfect for fixing your commit history without losing your changes.

---

## `git reset --hard` — Destroy and Forget

```bash
git reset --hard HEAD~1
```

> *"This commit was a disaster. I want to erase it — and all the changes it made."*

### What it does:

* Removes the last commit
* **Deletes all related changes** from your working directory and staging area

### Example Use Case:

You tried adding animations to your site using a sketchy CSS library, and everything broke. Now you want to go back to how things were — *clean*.

```bash
git reset --hard HEAD~1
```

 Be careful: this is **permanent** unless you've backed up your changes somewhere.

---

## BONUS TIP: What does `HEAD~1` mean?

Think of `HEAD` as your current position in the Git timeline.
`HEAD~1` means “one step before now.”
You can also use commit hashes:

```bash
git reset --soft abc1234
git reset --hard abc1234
```

---

## When to Use Which?

| Use Case                               | Command            | Keeps Files? | Keeps Staging? |
| -------------------------------------- | ------------------ | ------------ | -------------- |
| Want to **reword/fix** a commit        | `git reset --soft` |  Yes         |   Yes          |
| Want to **discard** changes completely | `git reset --hard` |  No          |   No           |

---

## Pro Tip: Use `git log` First

Before you reset, always take a look at your commit history:

```bash
git log --oneline
```

This helps you reset to exactly the point you want — no surprises.

---

## Final Thoughts

`git reset` gives you incredible power over your commit history — but with great power comes great responsibility.

> **Soft reset** = Director’s cut (edit before publishing)
> **Hard reset** = Delete the whole scene and start over

---

## Try this

> Open any project where you've made at least two commits.
> Run git log --oneline and pick a commit to reset to using git reset --soft.
> What changed? What stayed the same?
> Then try the same using git reset --hard — but only if you're okay losing those changes.
> Try running `ls -a` inside `.git` folder in your terminal and see what Git is quietly doing behind the scenes.

---
