# README
This Repository is for Second Study Vue.js + Ruby on Rails<br>
<br>
Referenced by<br>
https://bit.ly/2FJqOjk

- Frontend Vue.js
- Backend Ruby on Rails

## 環境
- Ruby 2.6.5
- Ruby on Rails 5.2.3
- Vue.js 2.6.11

## Railsをインストール

```
$ rails _5.2.3_ new rails-vue-sandbox -d postgresql
$ rails db:create
```

## Webpackerをインストール

```
// yarnのバージョンを確認する
$ yarn -v

$ rails webpacker:install
```

### 新規追加

- app/javascript/packs/application.js
- bin/webpack
- bin/webpack-dev-server
- bin/webpack-watcher
- config/webpack/development.js
- config/webpack/production.js
- config/webpack/shared.js
- yarn.lock

### 変更

- .gitignore
- config/environments/development.rb
- config/environments/production.rb
- package.json

## Vue.jsをインストール

```
$ rails webpacker:install:vue
```

### 新規追加

- app/javascript/packs/app.vue

```
# app/javascript/packs/app.vue

<template>
  <div id="app">
    Hello Vue!
  </div>
</template>
```

- app/javascript/packs/hello_vue.js

```
# app/javascript/packs/hello_vue.js

// Run this example by adding <%= javascript_pack_tag 'hello_vue' %> to the head of your layout file,
// like app/views/layouts/application.html.erb.
// All it does is render <div>Hello Vue</div> at the bottom of the page.

import Vue from 'vue'
import App from './app.vue'

document.body.appendChild(document.createElement('hello'))

new Vue({
  el: 'hello',
  template: '<App/>',
  components: { App }
})
```

### 変更

- config/webpack/shared.js
- package.json
- yarn.lock

## インデックス画面を作成

```
$ rails g controller Home index
```

```
# app/controllers/home_controller.rb
class HomeController < ApplicationController
  def index
  end
end

```

```
# app/views/home/index.html.erb
# => ビューは空にしておく

# app/views/layouts/application.html.erb

<!DOCTYPE html>
<html>
  <head>
    <title>RailsVueSandbox</title>
    <%= csrf_meta_tags %>
    <%= csp_meta_tag %>

    <%= stylesheet_link_tag    'application', media: 'all', 'data-turbolinks-track': 'reload' %>
    <%= javascript_include_tag 'application', 'data-turbolinks-track': 'reload' %>
  </head>

  <body>
    <%= yield %>
    <%= javascript_pack_tag 'hello_vue' %>
  </body>
</html>
```

```
# config/routes.rb

Rails.application.routes.draw do
  root to: 'home#index'
end
```

## JavaScriptをコンパイルする

```
$ bin/webpack
```

## 画面をロードする

```
$ rails s
```
