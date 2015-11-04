# Blade模版引擎

## 向视图传递变量

**使用with传递**

`with(key, value)`

```
$title = '文章标题1';
return view('articles.lists')->with('title',$title);
```

**使用view传递**

`view('articles.list', ['title' => $title])`

可以传递多个变量

**使用compact**

`view('articles.list', compact('title'));`

compact() 的字符串可以就是变量的名字，多个变量名用逗号隔开

## Blade基本用法

- `{!! $key !!}`: 使用一个变量
- `{{$key}}`: 使用一个变量，会将数据原样输出

### 布局

`@yield()`: 设置一个内容域@yield('content')

```
<div>
    @yield('content')
</div>
```

`@extends()`: 声明继承

`@extends('app')`

`@section('content') ... @endsection` 替换位置

```
@section('content')
<h1>{!! $title !!}</h1>
<p>{{ $intro }}</p>
@endsection 
```

### if else

```
@if($first == 'bool')
<h1>true</h1>
@else
<h1>false</h1>
@endif
```

`@unless()` 可以理解为 `if(! )`

### foreach()

```
@foreach( $first as $name)
<h1>{{$name}}</h1>
@endforeach
```

## Blade Template Commands

- {{ $var }} - Echo content
- {{ $var or 'default' }} - Echo content with a default value
- {{{ $var }}} - Echo escaped content
- {{-- Comment --}} - A Blade comment
- @extends('layout') - Extends a template with a layout
- @if(condition) - Starts an if block
- @else - Starts an else block
- @elseif(condition) - Start a elseif block
- @endif - Ends a if block
- @foreach($list as $key => $val) - Starts a foreach block
- @endforeach - Ends a foreach block
- @for($i = 0; $i < 10; $i++) - Starts a for block
- @endfor - Ends a for block
- @while(condition) - Starts a while block
- @endwhile - Ends a while block
- @unless(condition) - Starts an unless block
- @endunless - Ends an unless block
- include(file) - Includes another template
- @include(file, ['var' => $val,...]) - Includes a template, passing new variables.
- @each('file',$list,'item') - Renders a template on a collection
- @each('file',$list,'item','empty')- Renders a template on a collection or a different template if collection is empty.
- @yield('section') - Yields content of a section.
- @show - Ends section and yields its content
- @lang('message') - Outputs message from translation table
- @choice('message', $count) - Outputs message with language pluralization
- @section('name') - Starts a section
- @stop - Ends section
- @endsection - Ends section
- @append - Ends section and appends it to existing of section of same name
- @overwrite - Ends section, overwriting previous section of same name

- [参考](https://phphub.org/topics/1303)
- [Simple Blade](https://scotch.io/tutorials/simple-laravel-layouts-using-blade)
- [Laravel 模版](http://laravel-china.org/docs/5.0/templates)
