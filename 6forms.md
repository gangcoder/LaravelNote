# 表单illuminate/html

[illuminate/html](https://github.com/illuminate/html)

`composer require illuminate/html`


## 配置 illuminate/html

通过提供Service Provider和指定Facade！就可以将illuminate/html与Laravel结合

`config/app.php` 文件:

providers 中添加: `Illuminate\Html\HtmlServiceProvider::class,`

aliases 中添加: `'Form'      => Illuminate\Html\FormFacade::class,`


## 使用

```
@section('content')
    <h1>撰写新文章</h1>
    {!! Form::open() !!}
        <div class="form-group">
           {!! Form::label('title','标题:') !!}
           {!! Form::text('title',null,['class'=>'form-control']) !!}
       </div>
    {!! Form::close() !!}
@endsection
```

在页面生成 form 表单

### Form::open

指定提交路径

`{!! Form::open(['url'=>'article/store']) !!}`

### Form::text

1. Form::text 表示<input type='text' />，类比如 <input type='password' />等，可以参照着写。
1. 'title' 表示 name='title'
1. null 表示 value=''
1. 'class'=>'form-control' 表示class='form-control'，可以指定id，placeholder等一系列属性


## 内容接收

```
$input = $request->all();
return $input;
```

$request->get('title') 仅获取title值

### 数据入库

```
$input = $request->all();
Article::create($input); # 数据入库
return redirect('/');    # 页面跳转至首页
```


[参考](https://phphub.org/topics/1325)