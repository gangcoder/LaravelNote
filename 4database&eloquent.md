# 数据库

## 配置

`config/database.php`

env() 函数读取 `.env` 文件的数据

`.env` 保存数据库账目

## Migration

数据库管理工具

- migrate:install
- migrate:refresh
- migrate:reset
- migrate:rollback
- migrate:status

**创建表**

`php artisan make:migration create_articles_table --create='articles'`

`database/migrations` 目录下生成migration 文件

- up(): 执行 `php artisan migrate`时调用
- down(): 执行 `php artisan migrate rollback`时调用

### 修改数据库字段

1. `php artisan migrate:rollback`
1. 修改 `up()`
1. `php artisan migrate`

## 使用Eloquent

`php artisan make:model Article`

模型与数据库的命名遵循：数据表复数而model单数大写

Article Model创建后位于 `laravel/app/Article.php`

### tinker

tinker提供了一个Eloquent跟数据库表交互的命令行界面

`php artisan tinker`

```
$article = new App\Article # 实例化Article
$article->title = 'Router Views Controllers'; # 设置字段
$article->save()  # 保存设置
```

### 结果集处理

- `all()` 返回所有记录 `$articles = App\Article::all()`
- `find($id)` 查找一条记录 `$article = App\Article::find(1);`
- `toArray()` 将Eloquent对象转为数组 `$article = App\Article::find(1)->toArray();`
- `toJson()` 将Eloquent对象转为json `$article = App\Article::find(1)->toJson();`
- `where()` `$article = App\Article::where('title','=','Router Views Controllers')->get();`

### 数据更新

Eloquent默认是不允许直接更新数据,可以通过在Article这个model文件里面加一个$fillable数组进行允许

```
$article = App\Article::find(1);
$article->intro = 'Article 1 Intro Update!';
$article->save();
```

### 数据删除

delete() 方法

```
$article = App\Article::find(2);
$article->delete();
```

destroy() 方法

```
App\Article::destroy(3);
```

- [参考](https://laravist.com/article/12)
- [数据库](https://phphub.org/topics/1313)
- [migrations](http://laravel.com/docs/5.1/migrations)