# 表单验证

## Request表单验证

生成表单验证类 `php artisan make:request StoreArticleRequest`

生成的文件位于 `app/Http/Request`

### 添加验证规则

`authorize()`: 是否需要进行验证

`rules()`: 设置验证规则

```
public function rules()
{
    return [
        'title' => 'required',
        'content' => 'required'
    ];
}
```

### 应用验证规则

修改`ArticleController` 的 `store()`方法

```
public function store(Requests\StoreArticleRequest $request)
{
    $input = $request->all();
    //下面增加两行，顺便看看Request::get的使用
    $input['intro'] = mb_substr($request->get('content'),0,64);
 }   
```

将`StoreArticleRequest`类的实例传入store()方法，会自动检查我们是否需要进行表单验证

### 显示反馈错误

```
@if($errors->any())
    <ul class="alert alert-danger">
        @foreach($errors->all() as $error)
            <li>{{ $error }}</li>
        @endforeach
    </ul>
@endif
```

打印任何表单错误

显示中文错误信息, 修改文件`resources/lang/en/validation.php`

### 多个验证规则

`'title' => 'required | min:3`

用 | 隔开多个规则，: 表示规则的值

### 常用规则

```
'email' => 'required | email,
'password' => 'required | min:6'
```

## Validation验证

直接在ArticleController当中使用Validator::make()

`Validator::make(array $request,array $rules)`

```
$input = Request::all();
$validator = Validator::make($input, [
    'title' => 'required|min:3',
    'body' => 'required',
]);
```

通过判断`$validator->fails()` 验证是否通过

```
if ($validator->fails()) 
{
    # coding...         
}
```


- [http://laravel.com/docs/5.1/validation](http://laravel.com/docs/5.1/validation)
- [https://laravist.com/article/15](https://laravist.com/article/15)