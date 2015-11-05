# MVC的基本流程

1.注册路由 ---> 2.创建控制器 ---> 3. 控制器中通过模型获取数据 ---> 4.在视图中展示数据

## 注册路由

`Route::get('/','ArticleController@index');`

### 路由变量

`Route::get('articles/{id}','ArticleController@show');`

路由变量写在{}括号中，这个id对应我们等下写的show()方法的参数。

## 创建控制器

`php artisan make:controller ArticleController --plain`

--plain 不会生成额外代码

## 获取数据

```
use App\Article; # 引入模型

class ArticleController extends Controller
{

    public function index()
    {
        $articles = Article::all();
        return view('articles.index', compact('articles'));
    }
}
```

可以使用 `dd($var)` 测试数据

**findOrFail方法**

`$article = Article::findOrFail($id);`

findOrFail()表示首先尝试find，如果找不到就fail，抛出一个Eloquent Exception

## 展示数据

引入视图文件，并传入数据 `view('articles.index',compact('articles'));`

在`resources/views/articles/index.blade.php` 中展示数据

```
@extends('app')
@section('content')
 <h1>这是index.blade.php</h1>
@endsection
```

### abort

`abort(404)` 载入`resources/views/errors/404.blade.php`

### 添加链接

- `href="/articles/{{ $article->id }}"`
- `href="{{ action('ArticleController@show',[$article->id]) }}"`
- `href="{{ url('articles/',$article->id) }}"`


[参考](https://phphub.org/topics/1321)