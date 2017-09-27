# AngularでFLOUを採用する際のルール

## 概要
* cssのルールのベースとして、[FLOU](https://webnaut.jp/technology/20170407-2421/)を採用する

### ルール適用の優先度
1. 本記事記載の独自ルールを最優先とする
2. [FLOU](https://webnaut.jp/technology/20170407-2421/)に記載されているものに関しては、[flocss](https://github.com/hiloki/flocss)よりも優先する。
3. 上記の2つに存在しない項目に関しては、[flocss](https://github.com/hiloki/flocss)を採用する。


### ディレクトリ構成
* Angularのsrcの下にscssというディレクリを作成し、その下にFoundation、Layout、Object、Utilityというディレクトリを作成する

#### Foundation
* 基本的には[flocss](https://github.com/hiloki/flocss)に従う

> 基本的にコードは追加しない

引用元: 
[FLOCSSを扱いきれないあなたに贈る、スリムなCSS設計の話 | WebNAUT](https://webnaut.jp/technology/20170407-2421/)

* foundation.scssに記述する

#### Layout
* 基本的には[flocss](https://github.com/hiloki/flocss)と[FLOU](https://webnaut.jp/technology/20170407-2421/)に従う。
* IDセレクタは採用しない
* `l-*` プレフィックスをつけた命名を採用する
* layout.scssに記述する

#### Object
* 基本的には[FLOU](https://webnaut.jp/technology/20170407-2421/)に従う
* FLOCSSのComponentとProjectを統合したようなものにする
* object.scssに記述する

#### Utility
* 基本的には[flocss](https://github.com/hiloki/flocss)と[FLOU](https://webnaut.jp/technology/20170407-2421/)に従う
* プレフィックスとして `u-` をつける
* utility.scssに記述する
* 確実にスタイルを適用させるために `!important` を指定する
[CSSの設計 – FLOCSSをベースにしたファイルの構成と命名規則を考える ｜ Tips Note by TAM](https://www.tam-tam.co.jp/tipsnote/html_css/post10205.html)

### セレクタの多重階層化を回避する
* [FLOCSSを使ってCSSファイルを20,000行から9,000行にした話 - Qiita](https://qiita.com/Atsss/items/4f9d98fb1d0546539c09)の「深い階層のセレクタは使わない」を参照

### マルチクラスの使用
* [FLOCSSを使ってCSSファイルを20,000行から9,000行にした話 - Qiita](https://qiita.com/Atsss/items/4f9d98fb1d0546539c09)の「マルチクラスを積極的に使う」を参照


### 命名規則
* [flocss](https://github.com/hiloki/flocss)に従う。
* JavaScript のクラス命名規則については、[FLOCSSを使ってCSSファイルを20,000行から9,000行にした話 - Qiita](https://qiita.com/Atsss/items/4f9d98fb1d0546539c09)を参考にする。

### AngularのComponentとの兼ね合い
* 基本的には `src/scss` の下のディレクトリに存在するファイルで、スタイルを適用する。
* Component毎に設定が必要なスタイルにおいてのみ、各Componentの `*.component.scss` に個別のスタイルを記述する。

### Angularのディレクトリ構成
* 基本的には、Angular-CLIの構成に従う。


```
client
├── src
│   ├── app
│   │    ├──component名
│   │    │   ├── components(子componentはこの下さらに作成)
│   │    │   │     ├── hoge.component.html	
│   │    │   │     ├── hoge.component.scss
│   │    │   │     ├── hoge.component.spec.ts
│   │    │   │     ├── hoge.component.ts
│   │    │   │ 
│   │    │   ├── hoge-routing.module.ts(routingの設定)
│   │    │   ├── hoge.module.ts
│   │    │
│   │    ├── shared
│   │    │     ├── components(各componentで共通で使用するcomponent)
│   │    │     │
│   │    │     ├── pipes
│   │    │     │    ├──hoge.pipe.ts
│   │    │     │    ├──hoge.pipe.spec.ts
│   │    │     │      
│   │    │     ├── services
│   │    │          ├── api(サーバー側のAPIを叩くためのservice)
│   │    │          ├── util(ユーティリティ)
│   │ 
│   ├── assets(imgなど)
│   │    ├── img(画像)
│   │ 
│   ├── environments
│   │
│   ├── scss
│   │    ├── foundation
│   │    │    ├── foundation.scss
│   │    │        
│   │    ├── layout
│   │    │    ├── layout.scss
│   │    │    
│   │    ├── object
│   │    │    ├── object.scss
│   │    │ 
│   │    ├── utility
│   │         ├── utility.scss
│   │   
│   ├── favicon.ico
│   │
│   ├── index.html
│   │
│   ├── main.ts
│   │   
│   ├── polyfills.ts
│   │   
│   ├── styles.scss
│   │   
│   ├── tsconfig.app.json
│   │   
│   ├── tslint.json
│   │   
│   ├── tsconfig.spec.json
│   │   
│   ├── typings.d.ts
│        
├── e2e   
│        
├── karma.conf.js
│        
├── node_modules
│        
├── package.json
│        
├── protractor.conf.js
│        
├── tsconfig.json
│        
├── tslint.json
    
````

## 参考にさせていただいたサイト
[hiloki/flocss: CSS organization methodology.](https://github.com/hiloki/flocss)

[FLOCSSを扱いきれないあなたに贈る、スリムなCSS設計の話 | WebNAUT](https://webnaut.jp/technology/20170407-2421/)

[https://www.tam-tam.co.jp/tipsnote/html_css/post10205.html](https://www.tam-tam.co.jp/tipsnote/html_css/post10205.html)

[FLOCSSを使ってCSSファイルを20,000行から9,000行にした話 - Qiita](https://qiita.com/Atsss/items/4f9d98fb1d0546539c09)