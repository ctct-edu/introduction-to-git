## Step 2　初めてのリポジトリを作る

Git で編集するファイルは作業ツリーにあり、次のコミットに入れる変更はステージング領域に集めます。コミットすると、選んだ変更が履歴に記録されます。

1. ターミナルでプロジェクトのフォルダーに移動し、`git init` を実行します。`git status` でコミットがまだないことを確認します。
2. まず `src/index.html`、続いて `src` 内の残りのファイルをステージします。状態を確認して `Initial commit` を作り、作業ツリーがクリーンになったことを確認します。
3. VS Code の **Explorer** で `stack-overflown` フォルダー内に `README.md` を作り、指定された最初の内容を入れます。
4. **Source Control** の **Changes** でファイル横の `+` を選び、指定メッセージでコミットします。
5. README に開発者向けの内容を追加し、同様にステージして2回目のコミットを作ります。

### 原文のコマンド・入力例

```bash
cd /workspaces/stack-overflown
```

```bash
git init
```

```bash
git status
```

```bash
git add src/index.html
git add src/index.js
git add src/patterns.js
git add src/style.css
```

```bash
git add src/*
```

```bash
git status
```

```bash
git commit -m "Initial commit"
```

```bash
git status
```

```txt
README.md
```

```md
# Stack Overflown

Organize the falling blocks into the current debug pattern before the stack overflows! ⏳
```

```txt
Start game documentation
```

```md
## How to Develop

- `index.html` - the game container for playing
- `index.js` - the primary game logic
- `patterns.js` - the error patterns to match during gameplay
- `style.css` - the game formatting and styling
```

```txt
Start developer docs
```

[原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/2-step.md)
