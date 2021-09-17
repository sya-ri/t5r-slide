---
theme: seriph
background: https://images.pexels.com/photos/1072179/pexels-photo-1072179.jpeg
class: text-center
highlighter: shiki
title: t5r
---

# Yumemi Server-Side Intern
## @sya-ri

---

# 目次

- 目的
- 課題
- 設計
- 開発
  - PullRequest
  - Livewire について
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>


---

# 目次

- 目的 &nbsp; 👈
- 課題
- 設計
- 開発
  - PullRequest
  - Livewire について
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>


---

# 目的

- PHP をさわれるようにする。
- 動的型付け言語に慣れたい。
- 設計を行なって開発する経験を積む。
- テストを利用して開発する経験を積む。
- レビューをもらって保守性の高いコードを書く。

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
</style>


---

# 目次

- 目的
- 課題 &nbsp; 👈
- 設計
- 開発
  - PullRequest
  - Livewire について
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# 課題

## 「 PHP + Laravel で Twitter like なアプリを作る 」

<br>

|||
|---|---|
| 開発環境 💻 | PhpStorm |
| 実行環境 🔧 | Docker |
| 使用言語 🌏 | PHP |
| フレームワーク 🚀 | Laravel |
| 認証 🔐 | Laravel Breeze |
| インターフェース 👀 | Brade + Laravel Livewire |
| データベース 📦 | MySQL |

<br>



---

# 目次

- 目的
- 課題
- 設計 &nbsp; 👈
- 開発
  - PullRequest
  - Livewire について
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# 設計

- 要件定義
- データベース設計 - dbdiagram.io
- 画面設計 - figma.com
- URL設計

<style>
  li {
   	font-size: 1.2em;
  	padding-bottom: 0.4em;
  }
</style>



---

# 目次

- 目的
- 課題
- 設計
- 開発
  - PullRequest &nbsp; 👈
  - Livewire について
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# [開発 PR#1](https://github.com/sya-ri/t5r/pull/1)

CONTRIBUTING.md を追加

### ○ 概要

<br>

#### コミットメッセージ

```
(type): (title)
(description)
```

<br>

#### ブランチ

GitHub Flow を採用する。

- `master` は安定しており、デプロイ可能である。
- `master` に直接プッシュすることはできない。
- 作業を行う場合は、`master` からブランチを作成する。
- `master` へのマージはプルリクエストを介して行う。
- (プルリクエストのマージには２人以上の承認が必要。)


---

# [開発 PR#2](https://github.com/sya-ri/t5r/pull/2)
認証機能の追加

### ○ 概要

<br>

- Laravel Breeze の導入

<br>

### ○ 振り返り

<br>

- 導入するだけで認証周りのコードを自動生成してくれるので楽だった。
- 自動生成したコードによって、URL設計を追加することになった。
- 考慮していないカラムがあったので users テーブルの設計を変更することになった。


---

# [開発 PR#3](https://github.com/sya-ri/t5r/pull/3)
Pull Request に対してテストを走らせるようにした

### ○ 概要

<br>

- GitHubActions で PR をテストする。

<br>

### ○ 振り返り

<br>

- GitHubActions 自体は使ってきたので、ベースとなるワークフローファイルは作成できた。
- Docker に悩まされた。 (tty, docker-compose, ...)
- ```shell
  docker-compose exec -T mysql bash -c "mysqladmin --wait --count 60 ping || exit 1"
  ```
  という処理で MySQL の起動待機を行なっているが、50%くらいの確率で
  ```
  Connection refused
  ```
  エラーが出てしまう。
---

# [開発 PR#4](https://github.com/sya-ri/t5r/pull/4)
メッセージ一覧機能の追加

### ○ 概要

<br>

- Livewire の導入
- タイムラインページの追加
- メッセージ表示の追加
- いいね機能の仮追加
  - いいね数の表示はランダム。
  - 🖤 を押したら ❤️ に切り替わる。

<br>

### ○ 振り返り

<br>

- いいねの機能を仮追加してしまったため、無駄な変更を入れてしまった。
  - レビューの時に分かりにくくなるので、仮追加が必要かを考える。
  - Livewire の導入もいいね機能の実装時にすれば良かった。


---

# [開発 PR#5](https://github.com/sya-ri/t5r/pull/5)
依存関係のバージョンを更新

### ○ 概要

<br>

- compose, nodejs の依存関係の更新

<br>

### ○ 振り返り

<br>

- する必要はなかった。
- 依存関係の更新について話せたのでよかった。


---

# [開発 PR#6](https://github.com/sya-ri/t5r/pull/6)
いいね機能の追加

### ○ 概要

<br>

- 🖤 をクリックすると ❤️ になる。
- 自分のメッセージにはいいねできない。
- 🖤, ❤️ の隣にいいねの合計数を表示する。

<br>

### ○ 振り返り

<br>

- Livewire を使うことで、ボタン処理のために route で POST のハンドリングをしなくて良い。


---

# [開発 PR#7](https://github.com/sya-ri/t5r/pull/7)
メッセージ投稿機能の追加

### ○ 概要

<br>

- メッセージを入力して送信ボタンを押すことで、新しいメッセージを投稿できる。
- メッセージの見やすさのために、先頭・末尾の空白を削除する(trim)。
- 255文字以下のメッセージを送信できる。

<br>

### ○ 振り返り

<br>

- Livewire のおかげで時間をかけずに実装できた。
- アルファベット・日本語(UTF8)・絵文字(UTF8MB4) についてテストを書いたことが良かった。
  - 255文字 → 成功 / 256文字 → 失敗
  - 制限を設けるならギリギリのパターンについてのテストを書いておくと安心できる。



---

# 目次

- 目的
- 課題
- 設計
- 開発
  - PullRequest
  - Livewire について &nbsp; 👈
- デモ
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# Livewire について

メッセージ投稿機能

```php{all|7}
# timeline.blade.php
<x-app-layout>
    <!-- 省略 -->

    <div class="md:container md:mx-auto shadow-lg py-2">
        <div class="m-2">
            <livewire:create-message-form />
        </div>
        
        <!-- 省略 -->
        
    </div>
</x-app-layout>
```

- 使いたいところで Livewire コンポーネントを呼び出す。
- 今回の例では `create-message-form` という名前。

---

# Livewire について

メッセージ投稿機能

```php
use Livewire\Component;

class CreateMessageForm extends Component
{
    const MaxLength = 255;

    public $content = '';

    public function render()
    {
        return view('livewire.create-message-form');
    }

    public function onSubmit()
    {
        // 送信ボタンを押した時の処理
    }
}
```

- `Livewire\Component` というクラスを継承したクラスを作成する。
- `render()` というメソッドで `create-message-form.blade.php` を返す。


---

# Livewire について

メッセージ投稿機能

```php{all|11|14}
# create-message-form.blade.php
<div>
    @error('content')
        <span class="text-red-600 text-sm error">{{ $message }}</span>
    @enderror
    <div class="border border-gray-800">
        <textarea
        	class="block resize-none border-none w-full p-2"
            rows="4"
            maxlength="{{ \App\Http\Livewire\CreateMessageForm::MaxLength }}"
            wire:model.defer="content"
            type="text"
        ></textarea>
        <button class="border-t border-gray-800 bg-green-300 w-full" wire:click="onSubmit">
            <p class="text-lg text-center m-1">Submit</p>
        </button>
    </div>
</div>
```

- `wire:model` を指定すると、指定した名前のプロパティに代入してくれる。
- `wire:click` を指定すると、クリックした時にそのメソッドを呼び出してくれる。

---

# Livewire について

メッセージ投稿機能

```php
// テスト
public function test_message_can_be_created() {
    $user = User::factory()->create();
    $this->actingAs($user);
    $content = Str::random();

    $livewire = Livewire::test(CreateMessageForm::class, ['content' => $content]);
    $livewire->call('onSubmit');

    $message = Message::all()
        ->where('user_id', $user->id)
        ->where('content', $content)
        ->first();
    $this->assertNotNull($message);
}
```

- コンポーネント単位でテストする。
- メソッドを呼び出されたものとして、処理を行う。


---

# Livewire について

メッセージ投稿機能

### 内部

<br>

- `POST /livewire/コンポーネント名` というリクエストを投げてくれる。
- `wire.model.defer` という指定をするとボタンを押した時に送信する。
  - `wire.model` だと変更する度にリクエストを投げる（更新処理のため）。

<br>

### 利点

<br>

- コンポーネントを作成して、その処理をクラス内に記述できる。
- `js` を書く必要がない。
  - クライアント側で完結させたい場合は書く必要がある。
- めちゃめちゃ簡単に実装ができる。


---

# 目次

- 目的
- 課題
- 設計
- 開発
  - PullRequest
  - Livewire について
- デモ &nbsp; 👈
- 振り返り

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# デモ

- AWS EC2 でアプリを動作
  - Yumemi の VPN を通すことでアクセス可能
- AWS RDS でデータベースを管理
  - EC2 からのみアクセス可能で、直接のアクセスはできない。
- ウェブページ

---

# 目次

- 目的
- 課題
- 設計
- 開発
  - PullRequest
  - Livewire について
- デモ
- 振り返り &nbsp; 👈

<style>
  li {
   	font-size: 1.2em;
    margin-left: 50px;
  	padding-bottom: 0.4em;
  }
  li li {
  	font-size: 1em;
    padding-bottom: 0.1em;
  }
</style>

---

# 振り返り

- インターンの目的を達成できたので、とても良かった。
- 食わず嫌いしていた PHP が３割くらい好きになった。
- Livewire がとても楽だったので、個人的に使いたいと思った。

<br>

#### → とても良かった！！！！
