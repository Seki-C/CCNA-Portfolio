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
git remote add origin https://github.com/Seki-C/CCNA-Portfolio.git

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

## GitHubとのSSH接続設定（推奨）

HTTPSではなくSSH接続を使用すると、パスワード入力が不要になり、より安全に操作できます。

### 1. SSHキーペアの生成

1. コマンドプロンプトまたはPowerShellを開きます
2. 以下のコマンドを実行します（メールアドレスは自分のGitHubアカウントのメールアドレスに置き換えてください）：
   ```bash
   ssh-keygen -t ed25519 -C "your_email@example.com"
   ```
3. キーの保存場所を尋ねられたら、デフォルトの場所（通常は`C:\Users\<ユーザー名>\.ssh\id_ed25519`）でEnterキーを押します
4. パスフレーズの入力を求められたら、セキュリティを高めるためにパスフレーズを設定することをお勧めします（または空のままEnterキーを押すこともできます）

### 2. SSHキーをSSHエージェントに追加

1. SSHエージェントを起動します：
   ```bash
   # PowerShellの場合
   Get-Service -Name ssh-agent | Set-Service -StartupType Automatic
   Start-Service ssh-agent
   
   # コマンドプロンプトの場合
   start-ssh-agent.cmd
   ```

2. 生成した秘密鍵をSSHエージェントに追加します：
   ```bash
   ssh-add ~/.ssh/id_ed25519
   ```

### 3. 公開鍵をGitHubアカウントに追加

1. 公開鍵をクリップボードにコピーします：
   ```bash
   # PowerShellの場合
   Get-Content ~/.ssh/id_ed25519.pub | clip
   
   # コマンドプロンプトの場合
   type %userprofile%\.ssh\id_ed25519.pub | clip
   ```

2. GitHubにログインし、右上のプロフィールアイコンをクリックして「Settings」を選択します
3. 左側のサイドバーで「SSH and GPG keys」をクリックします
4. 「New SSH key」または「Add SSH key」ボタンをクリックします
5. 「Title」フィールドに、このキーを識別するための名前（例：「Work Laptop」）を入力します
6. 「Key」フィールドに、クリップボードにコピーした公開鍵を貼り付けます
7. 「Add SSH key」ボタンをクリックして保存します

### 4. SSH接続のテスト

以下のコマンドを実行して、GitHubとのSSH接続をテストします：
```bash
ssh -T git@github.com
```

初回接続時は、サーバーの認証確認が表示されます。「yes」と入力してEnterキーを押します。
成功すると、「Hi username! You've successfully authenticated, but GitHub does not provide shell access.」というメッセージが表示されます。

### 5. リモートリポジトリのURLをSSH形式に変更（既存のリポジトリの場合）

既にHTTPSでリモートリポジトリを設定している場合は、以下のコマンドでSSH形式に変更できます：

```bash
# 現在のリモートURLを確認
git remote -v

# リモートURLをSSH形式に変更（ユーザー名は自分のGitHubユーザー名に置き換えてください）
git remote set-url origin git@github.com:ユーザー名/CCNA-Portfolio.git
```

### 6. 新しいリポジトリをSSHで接続する場合

新しいリポジトリをクローンする場合は、HTTPSのURLではなくSSHのURLを使用します：
```bash
git clone git@github.com:ユーザー名/リポジトリ名.git
```

---

このポートフォリオをGitHubで公開することで、以下のメリットがあります：

1. 学習の進捗を可視化できる
2. 他の学習者と知識を共有できる
3. 将来の雇用主や同僚に技術的な知識とスキルをアピールできる
4. バージョン管理により、学習の履歴を追跡できる
5. どこからでもアクセスして学習を継続できる

定期的に更新し、学習の成果を記録していきましょう！