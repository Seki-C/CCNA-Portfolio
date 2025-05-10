# GitHubリポジトリのセットアップ手順

このドキュメントでは、CCNA学習ポートフォリオをGitHubリポジトリとして公開するための手順を説明します。

## 前提条件

1. [Gitがインストール](https://git-scm.com/downloads)されていること
2. [GitHubアカウント](https://github.com/join)を持っていること
3. 基本的なGitコマンドの知識があること

## 手順

### 1. GitHubでリポジトリを作成する

1. GitHubにログインします
2. 右上の「+」ボタンをクリックし、「New repository」を選択します
3. リポジトリ名を「CCNA-Portfolio」（または任意の名前）に設定します
4. 説明（Description）に「CCNA試験の学習ポートフォリオ」などと入力します
5. リポジトリを「Public」に設定します（学習成果を共有するため）
6. 「Initialize this repository with a README」のチェックを外します（すでにREADME.mdを作成済みのため）
7. 「Create repository」ボタンをクリックします

### 2. ローカルリポジトリを初期化する

ターミナル（コマンドプロンプトまたはPowerShell）を開き、以下のコマンドを実行します：

```bash
# CCNA-Portfolioディレクトリに移動
cd CCNA-Portfolio

# Gitリポジトリを初期化
git init

# すべてのファイルをステージング
git add .

# 最初のコミットを作成
git commit -m "Initial commit: CCNA Portfolio structure"
```

### 3. ローカルリポジトリをGitHubに接続してプッシュする

GitHubで作成したリポジトリのURLを使用して、以下のコマンドを実行します：

```bash
# リモートリポジトリを追加（URLは自分のGitHubリポジトリのURLに置き換えてください）
git remote add origin https://github.com/yourusername/CCNA-Portfolio.git

# ローカルリポジトリをGitHubにプッシュ
git push -u origin main
```

注意: Gitの設定によっては、デフォルトのブランチ名が「main」ではなく「master」の場合があります。その場合は、上記のコマンドの「main」を「master」に置き換えてください。

### 4. GitHubでリポジトリを確認する

ブラウザでGitHubのリポジトリページを開き、すべてのファイルとディレクトリが正しくアップロードされていることを確認します。

## 定期的な更新

学習を進めながら、ポートフォリオを定期的に更新し、GitHubにプッシュすることをお勧めします：

```bash
# 変更をステージング
git add .

# コミットを作成（メッセージは具体的な内容に）
git commit -m "Add notes on OSI model and TCP/IP model"

# GitHubにプッシュ
git push
```

## GitHub Pagesの設定（オプション）

GitHubでポートフォリオをウェブサイトとして公開したい場合は、GitHub Pagesを設定することができます：

1. GitHubのリポジトリページで「Settings」タブをクリックします
2. 左側のメニューから「Pages」を選択します
3. 「Source」セクションで、「main」ブランチと「/(root)」フォルダを選択します
4. 「Save」ボタンをクリックします
5. 数分後、ポートフォリオがウェブサイトとして公開されます（URLは設定ページに表示されます）

## 参考リソース

- [Git公式ドキュメント](https://git-scm.com/doc)
- [GitHub Guides](https://guides.github.com/)
- [GitHub Pages](https://pages.github.com/)
- [Markdown記法](https://docs.github.com/ja/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

---

このポートフォリオをGitHubで公開することで、以下のメリットがあります：

1. 学習の進捗を可視化できる
2. 他の学習者と知識を共有できる
3. 将来の雇用主や同僚に技術的な知識とスキルをアピールできる
4. バージョン管理により、学習の履歴を追跡できる
5. どこからでもアクセスして学習を継続できる

定期的に更新し、学習の成果を記録していきましょう！