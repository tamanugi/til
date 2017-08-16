# Elm+Phoenixの開発環境を構築する


## Phoenixプロジェクトの作成
```
$ mix phx.new elm_test
$ cd elm_test
```

## Elmのインストール

```
$ mkdir assets/elm
$ cd assets/elm
$ elm package install elm-lang/html -y
```

## Elm-Brunchのインストール

```
$ cd assets
$ npm install --save-dev elm-brunch
```

brunch-config.jsonの修正

```diff
@@ -37,7 +37,7 @@ exports.config = {
   // Phoenix paths configuration
   paths: {
     // Dependencies and current project directories to watch
-    watched: ["static", "css", "js", "vendor"],
+    watched: ["static", "css", "js", "vendor", 'elm'],
     // Where to compile files to
     public: "../priv/static"
   },
@@ -47,6 +47,11 @@ exports.config = {
     babel: {
       // Do not use ES6 compiler in vendor code
       ignore: [/vendor/]
     },
+    elmBrunch: {
+      elmFolder: 'elm',
+      mainModules: ['Main.elm'],
+      outputFolder: '../js'
+    }
   },
```

## Main.elmの作成

```
$ touch assets/elm/Main.elm
```

```elm
module Main exposing (..)
import Html exposing (text, Html)
main : Html a
main =
  text "Hello Foo"
```

## app.jsとindex.html.eexの修正

app.js

```
$ git diff assets/js/app.js
--- a/assets/js/app.js
+++ b/assets/js/app.js
@@ -19,3 +19,10 @@ import "phoenix_html"
 // paths "./socket" or full ones "web/static/js/socket".

 // import socket from "./socket"
+
+import Elm from './main';
+const elmDiv = document.querySelector('#elm-target');
+if (elmDiv) {
+  Elm.Main.embed(elmDiv);
+}
+
```

index.html.eex

```
$ git diff lib/katareru_web/templates/page/index.html.eex  
diff --git a/lib/katareru_web/templates/page/index.html.eex b/lib/katareru_web/templates/page/index.html.eex
index 0988ea5..3c4e86e 100644
--- a/lib/katareru_web/templates/page/index.html.eex
+++ b/lib/katareru_web/templates/page/index.html.eex
@@ -1,3 +1,4 @@
+<div id="elm-target"></div>
 <div class="jumbotron">
   <h2><%= gettext "Welcome to %{name}!", name: "Phoenix" %></h2>
   <p class="lead">A productive web framework that<br />does not compromise speed and maintainability.</p>
```

## 実行

```
$ mix phx.server
```

