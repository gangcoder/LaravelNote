# 路由，控制器与视图

## 路由

`app/Http/routes.php`

以相对网站目录和HTTP方式进行路由

### 参数

```
$router->get('users/{name?}', function($name = 'Gey') {
    return 'Hello '.$name;
});
```

## 视图

`resources/views/`

使用blade模版引擎

使用视图文件 `view('articles.lists')`, 则相应文件为 `resources/views/articles/lists.blade.php`

view()方法会默认从views文件夹查找视图文件

## 控制器

`app/Http/Controllers`

使用控制器 `Route::get('/', 'ArticleController@index');`

## 操作流程

1. 在routes.php中注册路由
2. 创建对应的控制器
3. 在控制器对应方法中加载视图


[参考](https://phphub.org/topics/1302)