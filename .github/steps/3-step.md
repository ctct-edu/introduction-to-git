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

### 画面での確認

- `git log` が画面を占有した場合は `q` で入力待ちに戻ります。`<commit id>` は、表示されたコミットの識別子に山括弧ごと置き換えます。
- **Source Control** の **Graph** で、コミット名をクリックすると、そのコミットで変更したファイルが表示されます。最後に `main` に戻り、**Explorer** に `README.md` があることを確認します。

[原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/3-step.md)
