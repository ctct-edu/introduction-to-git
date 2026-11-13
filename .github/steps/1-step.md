## Step 1　Git のバージョン管理を知る

バージョン管理を使うと、ファイル名に「最終版」を付けて管理する代わりに、変更履歴を記録し、必要な時点に戻れます。Git は分散型のため、各作業者が履歴を持ち、通常の記録や確認はオフラインでもできます。

1. 最初の Issue の **Open in GitHub Codespaces** を開き、表示された所有者名とリポジトリ名が自分の演習用コピーと一致することを確認します。**Create new codespace**（画面によっては **Create codespace**）を選びます。

   [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/{{full_repo_name}}?quickstart=1)
2. ブラウザー版 VS Code が開いたら、左下に Codespaces の接続名が出るまで待ちます。「このフォルダー内のファイルの作成者を信頼しますか？」と表示された場合は、自分の演習用コピーから開いた環境であることを確認し、**フォルダーを信頼して続行**（**Trust Folder & Continue**）を選びます。
3. 左側の **Explorer**（エクスプローラー）で `stack-overflown` → `src` → `index.html` を開きます。`index.html` を右クリックして **Show Preview** を選び、ゲームが表示されることを確認します。`stack-overflown` が表示されない場合は、その時点で講師に知らせてください。
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

### 画面での確認

- ブラウザー上部で演習 Issue を開いたタブは残します。Codespace の作成画面では **Repository** に自分のユーザー名／演習名が表示されていることを確認し、緑色の **Create codespace** を押します。
- VS Code の左端にある書類のアイコンが **Explorer** です。左のファイル一覧で `stack-overflown` → `src` → `index.html` を探します。ターミナルはエディターの下に表示されます。
- `git --version` でバージョンが表示され、設定一覧で `user.name` と `user.email` が自分の入力値になっていることを確認します。

[原文](https://github.com/skills/introduction-to-git/blob/main/.github/steps/1-step.md)
