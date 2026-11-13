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

### 画面での確認

- **Explorer** の `stack-overflown/src` にある2つのファイルを使います。編集後は保存してからターミナルで `git diff` を実行します。
- 差分では、削除した行に `-`、追加した行に `+` が付きます。**Source Control** で `+` を押したあとは **Staged Changes** のファイルを開いて確認します。

[原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/4-step.md)
