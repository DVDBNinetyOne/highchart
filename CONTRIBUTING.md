# Working together on this repo

This is a small team working on a single large `index.html` file, so the
biggest risk isn't git mechanics — it's two or more people editing the same
function differently at the same time. Git will happily merge that without
complaint even though the result is broken. These habits keep that from
happening.

## Before you start a session

```bash
git pull origin redesign/simplified-ui
```

Always pull first, even if you were "just working on it five minutes ago."
Someone else may have pushed since.

## While you work

- Give a quick heads-up in chat before touching a section that might overlap
  (e.g. "working on the CMS config panel now"). Ten seconds of warning avoids
  most real conflicts.
- Commit and push in small, frequent chunks rather than one big change at the
  end of the day. Smaller commits mean smaller, easier-to-resolve conflicts
  if they do happen — and less work lost if something goes wrong.

## When you're done with a chunk

```bash
git add index.html
git commit -m "Short description of what changed and why"
git pull origin redesign/simplified-ui   # in case something landed while you worked
git push origin redesign/simplified-ui
```

If `git pull` reports a conflict, don't panic — it means someone else touched
the same lines. Open the file, look for the `<<<<<<<` / `=======` / `>>>>>>>`
markers, decide which version (or combination) is correct, remove the
markers, then commit and push as normal.

## If conflicts start happening often

That's a sign to add a bit more process — e.g. opening a quick PR for review
before merging into `redesign/simplified-ui`, or branch protection requiring
PRs. Worth revisiting sooner rather than later once a third person is
regularly working in the same file — more concurrent editors means more
chances to silently overlap.
