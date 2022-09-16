# Git Blueprints

---

> How to set up **git** and **conventional commits** with the help of the tools
> like (**husky, ...**) for enterprise development. The configuration of the tools will
> improve the **git** common **standards**.

## Husky

> What is **Husky**? It is a tool witch help you to use **git hooks**, it will improve your commits.
> Wisit [Husky Website](https://github.com/typicode/husky#readme).

### How to set up husky

1. Installation
    ```
    npm install husky -D
    npm set-script prepare "husky install"
    npm run install (prepare script will run automaticly)
    ```
2. Add hooks (git)
    ```
    npx husky add .husky/pre-commit "npm test"
    
    npx husky add .husky/commit-msg 
    paste in the ./husky/commit-msg file =>
    if ! head -1 "$1" | grep -qE "^(feat|fix|chore|docs|test|style|refactor|perf|build|ci|revert)(\(.+?\))?: .{1,}$"; then
    echo "Aborting commit. Your commit message is invalid." >&2
    exit 1
    fi
    if ! head -1 "$1" | grep -qE "^.{1,88}$"; then
    echo "Aborting commit. Your commit message is too long." >&2
    exit 1
    fi

    git add . 
    ```
3. Make a commit
    ```
   git commit -m "Keep calm and commit"
   "npm test" will run every time you commit
   ```