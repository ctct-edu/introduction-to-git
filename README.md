# 演習01　Git を使ってみる

ゲームのサンプルを使い、ターミナルと VS Code の両方で Git を練習します。変更履歴、差分、ブランチを順に扱います。Git とターミナルが初めての方も参加できます。教材の目安は60分未満です。

## 始め方

1. 講師から案内された日本語版テンプレートの GitHub ページを開きます。**Use this template** → **Create a new repository** を選び、**Owner** と公開範囲を確認して **Create repository** を選びます。
2. 20秒ほど待って再読み込みします。自分のコピーの **Issues** または **README** に出る案内に合わせて、この資料の同じ番号を開きます。
3. ファイル名、ブランチ名、コード、指定コメントは掲載どおりに入力します。操作後は GitHub 上で次の案内を確認します。

[GitHub Skills の原文 README](https://github.com/skills/introduction-to-git) · [教材のライセンス](LICENSE)

## Step 1　Git のバージョン管理を知る

バージョン管理を使うと、ファイル名に「最終版」を付けて管理する代わりに、変更履歴を記録し、必要な時点に戻れます。Git は分散型のため、各作業者が履歴を持ち、通常の記録や確認はオフラインでもできます。

1. 最初の Issue の **Open in GitHub Codespaces** から、自分の教材コピーを対象に **Create Codespace** を選びます。
2. ブラウザー版 VS Code の **Explorer** で `src/index.html` を右クリックし、**Show Preview** でゲームを開きます。
3. ターミナルが表示されていなければ、`Ctrl+Shift+P` から `View: Toggle Terminal` を実行します。
4. コマンド例の順に、Git のバージョンとヘルプを表示し、コミットに記録する名前とメールアドレスを設定します。例の `First Last` と `me@example.com` は自分の値に置き換えます。公開用には GitHub の noreply アドレスを利用できます。
5. 設定を一覧で確認し、Issue に次の案内が表示されるのを待ちます。

### 原文のコマンド・入力例

```bash
git --version
```

```bash
git --help
```

```bash
git config --global user.name "First Last"
```

```bash
git config --global user.email "me@example.com"
```

```bash
git config --global --list
```

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/1-step.md)

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

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/2-step.md)

## Step 3　Git の変更履歴を確認する

コミットには識別用のハッシュ、直前のコミットへの参照、作成者、日時、変更を説明するメッセージが記録されます。

1. `git log`、`git log --oneline`、`git log --graph --oneline` を順に実行し、詳しい履歴、1行表示、グラフの違いを見ます。
2. `Initial commit` の ID をコピーし、`git checkout <commit id>` の山括弧を含む部分を実際の ID に置き換えて実行します。README が表示されなくなることを確認します。
3. `git checkout main` で現在のブランチに戻り、README が再び表示されることを確認します。
4. **Source Control** で **Changes** の見出しを右クリックし、**Graph** を表示します。コミットをクリックして、変更されたファイルを確認します。

### 原文のコマンド・入力例

```bash
git log
```

```bash
git log --oneline
```

```bash
git log --graph --oneline
```

```bash
git checkout <commit id>
```

```bash
git checkout main
```

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/3-step.md)

## Step 4　変更前と変更後を比較する

差分（diff）では追加や削除を行ごとに確認できます。ステージする前と後では、比較する対象が変わります。

1. `src/index.html` の20行目付近にある `info-section` を、下のコード例に従って置き換えます。現在のスコアと最高スコアを表示し、ステータス表示を取り除きます。
2. `git diff src/index.html` を実行し、変更を確認します。ステージしたあとに同じコマンドを実行し、表示がなくなることを確かめます。
3. `git diff --staged src/index.html` でステージ済みの差分を確認し、指定のメッセージでコミットします。
4. `src/patterns.js` の3行目付近にある `Null Pointer` の定義をコード例に従って変更します。
5. **Source Control** の **Changes** でファイルをダブルクリックして差分を開きます。ステージしたあと、**Staged Changes** 側からも差分を開き、指定のメッセージでコミットします。

### 原文のコマンド・入力例

```diff
+ This is a line that was added
- This is a line that was removed
```

```txt
<div class="info-section">
   <h3>Current Score</h3>
   <div class="score" id="score">0</div>
   <h3>High Score</h3>
   <div class="high-score" id="high-score">0</div>
</div>
```

```bash
git diff src/index.html
```

```bash
git add src/index.html
```

```bash
git diff src/index.html
```

```bash
git diff --staged src/index.html
```

```md
git commit -m "Add element for showing high score"
```

```txt
{
  name: "Null Pointer",
  pattern: [
    [0, 1, 1, 1, 0],
    [0, 1, 0, 1, 0],
    [0, 1, 1, 1, 0],
    [0, 0, 1, 0, 0],
    [0, 0, 1, 0, 0],
  ],
},
```

```txt
Make null pointer pattern easier to complete
```

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/4-step.md)

## Step 5　ブランチを使って変更を進める

ブランチを使うと、安定した `main` から作業を分けて機能を開発できます。マージで作業を取り込みます。分岐先までポインターを進めるだけで済む場合はファストフォワードになります。

1. 履歴グラフを表示し、現在は一本道であることを確認します。`fix-incomplete-high-score` を作成して切り替えます。
2. コード例に従い、`src/index.js` に最高スコアの変数を追加し、保存値の読み込みを追加し、`updateScore` を変更します。各変更を個別にコミットします。
3. グラフで作業ブランチに3コミット増え、`HEAD` が作業中の位置を示していることを確認します。`main` に戻り、例の `--no-ff` 付きコマンドでマージします。グラフを確認し、作業ブランチを削除します。
4. VS Code の左下のブランチ名から **Create new branch...** を選び、`add-level-counter` を作ります。
5. コード例に沿って、`src/index.html` にレベルの表示を追加し、`src/index.js` に変数を追加し、`checkPatternMatch` を更新します。それぞれコミットします。
6. **Graph** で両方の作業履歴を確認します。左下から `main` に戻り、**Source Control** の `...` → **Branch** → **Merge...** で作業ブランチをマージします。ファストフォワードになったことを確認し、**Delete Branch...** で作業ブランチを削除します。

### 原文のコマンド・入力例

```bash
git log --all --graph --oneline
```

```bash
git branch fix-incomplete-high-score
git checkout fix-incomplete-high-score
```

```bash
git branch --list
```

```js
let highScore = 0;
```

```bash
git add src/index.js
git commit -m "Add new variable for tracking high score"
```

```js
// Load high score from localStorage
highScore = parseInt(localStorage.getItem("stackOverflownHighScore")) || 0;
document.getElementById("high-score").textContent = highScore;
```

```bash
git add src/index.js
git commit -m "Add loading of stored high score"
```

```js
function updateScore() {
  document.getElementById("score").textContent = score;

  // Update high score if current score exceeds it
  if (score > highScore) {
    highScore = score;
    document.getElementById("high-score").textContent = highScore;
    localStorage.setItem("stackOverflownHighScore", highScore);
  }
}
```

```bash
git add src/index.js
git commit -m "Add logic to keep track of highest score"
```

```bash
git log --all --graph --oneline
```

```bash
git checkout main
```

```bash
git merge --no-ff fix-incomplete-high-score -m "Fix high score tracker"
```

```bash
git log --all --graph --oneline
```

```bash
git branch --delete fix-incomplete-high-score
```

```txt
add-level-counter
```

```diff
<h3>Level</h3>
<div class="score" id="level">1</div>
```

```bash
Add element to display current level
```

```js
let level = 1;
let patternsCleared = 0;
```

```bash
Add variables for level and clear counter
```

```js
function checkPatternMatch() {
  for (let startRow = 0; startRow <= ROWS - PATTERN_SIZE; startRow++) {
    for (let startCol = 0; startCol <= COLS - PATTERN_SIZE; startCol++) {
      if (matchesPattern(startRow, startCol)) {
        clearPattern(startRow, startCol);
        score += 100;
        patternsCleared++;
        if (patternsCleared % 5 === 0) {
          level++;
          dropInterval = Math.max(200, 1000 - (level - 1) * 100);
          document.getElementById("level").textContent = level;
        }
        updateScore();
        setNewTargetPattern();
        return;
      }
    }
  }
}
```

```bash
Add logic to calculate level
```

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/5-step.md)

## Step 6　Git で共同作業する流れを知る

リポジトリをクローンして手元に複製し、ブランチで変更を作り、プッシュで共有先へ送ります。共同作業者は変更を取り込めます。取り込みを提案するときはプルリクエストを使います。

最初の Issue の「Git のどの機能が気に入りましたか」という質問に回答します。選択肢は、無料でオープンソース、オフラインで使える、複数の OS で使える、履歴を詳しく追える、最終版 ZIP を増やさなくてよい、の5つです。GitHub 上に表示されるチェック欄を使います。

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/6-step.md)

## 振り返り

Git の作成者情報を設定し、リポジトリとコミットを作り、履歴や差分を調べました。ブランチで機能を開発してマージし、共同作業の基本を確認しました。作業を終えたら Codespace を停止します。

[このステップの原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/x-review.md)
