# queryScope 和 setAttribute

**使用场景**

数据在存入数据库的时候需要进行预先处理

## setAttributes

Article.php 文件中添加

```
public function setPublishedAtAttribute($date)
{
    $this->attributes['published_at'] = Carbon::createFromFormat('Y-m-d',$date);
}
```

函数名命名: set+字段名+Attribute，使用驼峰法


## queryScope

Article.php 文件中添加

```
public function scopePublished($query)
{
    $query->where('published_at','<=',Carbon::now());
}
```

在 ArticleController 可以按如下方式使用

```
$articles = Article::latest()->published()->get();
```

- - [https://laravist.com/article/16](https://laravist.com/article/16)