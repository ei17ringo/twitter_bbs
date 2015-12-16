# twitter_bbs

## 以下の様なエラーが発生した時（Undefined~）

Notice:  Undefined variable: $_POST['name'] in /Applications/XAMPP/xamppfiles/htdocs/twitter_bbs/join/index.php on line 87

## 原因
存在していない変数の中身を取り出して表示しようとしているので「定義されていない変数」と認識されエラーになっています。
上の例だと、$_POSTはPOST送信されている時以外は存在しないので、最初に画面を表示した時に現れることが多いです。

## 対応策
POST送信されているか、されていないかで存在の有無が変わってしまう$_POST変数を直接表示に使うよりも、先に変数を自分で定義し、代入することで$_POST変数の中身を表示します

## 例
まずは変数を自分で定義します

    $name=''; //初期値に空文字を代入しておく
    
    //isset関数で存在を確認し、存在した時だけ代入処理
    if (isset($_POST['name])){
      $name = $_POST['name];
    }
    
    //表示する時は、自分で定義した変数を使用
    echo $name;
    

こうすると、$_POST変数が存在しない時は空文字を表示し、存在する場合は$nameに代入された値を表示できるのでUndefined variableというエラーメッセージを解消できます。
