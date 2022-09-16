[![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](https://github.com/commitizen/cz-cli)

# Git Blueprints

---

> How to set up **git** and **conventional commits** ([about con. commits](https://www.conventionalcommits.org/en/v1.0.0/)) 
> with the help of the tools
> like (**husky, commitizen**) for enterprise development. The configuration of the tools will
> improve the **git** common **standards**.

## Husky

> What is **Husky**? It is a tool witch help you to use **git hooks**, 
> it will improve your commits and can prevent bad commits.
> For more information visit [Husky Website](https://github.com/typicode/husky#readme).

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
    npx husky add .husky/commit-msg "(every command you want)"
    git add . 
    ```
3. Make a commit
    ```
   git commit -m "feat(button): Implemented button"
   "npm test (your commands in pre-commit hook)" will run every time you commit
   ```
   
## Commitlint

> Is a cli tool, which parses the commit message against 
> **conventional commit** specification ([more about con. commits](https://www.conventionalcommits.org/en/v1.0.0/)).

### How to set up

1. Installation
   ```
   npm i @commitlint/cli -D
   npm i @commitlint/config-conventional -D
   ```
2. Add to [husky](#husky) commit-msg hook
   ```
   npx husky add .husky/commit-msg "npx --no -- commitlint --edit $1"
   ```
3. Make a commit
   ```
   git add .
   git commit -m "Bad commit msg" => Error
   git commit -m "feat(button): implemented button" => Success, commit msg fallows conventional commit spec.
   ```

## Commitizen

> Is a tool (cli) witch defines a standard way of committing, it will help to write the commits in conventional style. 
> For more information visit [Commitizen Website](https://github.com/commitizen/cz-cli). 

### How to set up commitizen

1. Installation
   ```
   npm install -g commitizen
   ```
2. Making your repo Commitizen friendly
   ```
   commitizen init cz-conventional-changelog --save-dev --save-exact
   ```
3. Make a commit
   ```
   git add .
   git cz
   ```
