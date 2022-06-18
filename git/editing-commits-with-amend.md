# Editing Commits with Amend

This is a useful workflow that I learned while watching [helloitsrufio](https://twitch.tv/helloitsrufio)'s stream, a nifty little hack to earn more of the coveted green push squares and playing The Game™.

```git
git add .
git commit -m "super cool commit message"
git commit --amend --date="yyyy-mm-dd"
(To escape out of vim hell) Esc + :wq + Enter
git push
```

In the name of formalities, I learned the `amend` flag let's you modify an existing commit message, in the case of misspelling a word or forgetting to include important information. Without the `date` flag, it will modify your latest commit.

After entering the amended commit, Vim will open up and leave you with no obvious way to exit the CLI editor. In order to get back to the terminal prompt, you'll need to hit `Esc`, type `:wq`, and press `Enter`. Once back in the terminal, you can finish off your workflow with `git push`.