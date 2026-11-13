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

### 画面での確認

- ブランチ名は VS Code の左下で確認します。最高スコアの変更中は `fix-incomplete-high-score`、レベル表示の変更中は `add-level-counter` です。
- コミット後、左の **Source Control** の **Graph** で指定のコミットメッセージを確認します。マージ前に左下が `main` であること、マージ後は変更が履歴に含まれることを確認します。

[原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/5-step.md)
