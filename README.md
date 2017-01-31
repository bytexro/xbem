# B.E.M FRAMEWORK

```
____            _                       ____                                        _         
| __ )   _   _  | |_    ___  __  __     |  _ \    ___    _ __ ___     __ _   _ __   (_)   __ _
|  _ \  | | | | | __|  / _ \ \ \/ /     | |_) |  / _ \  | '_ ` _ \   / _` | | '_ \  | |  / _` |
| |_) | | |_| | | |_  |  __/  >  <      |  _ <  | (_) | | | | | | | | (_| | | | | | | | | (_| |
|____/   \__, |  \__|  \___| /_/\_\     |_| \_\  \___/  |_| |_| |_|  \__,_| |_| |_| |_|  \__,_|
        |___/                                                                                 
```
### by Prisecaru Bogdan



## Why should we use this?
---
- Easy and intuitive mixins for writing [B.E.M](https://en.bem.info/methodology/) classes
- Optimized output CSS
- No need for more then 1(one) class per element (except +state classes)
- No nesting beyond level 1(one) (except +state classes)


## Installation
---

* In your terminal:
```
npm install --save xbem
```
* In your webpack project, use 'sass-loader' with the following option:

webpack.config.js
```
{
  loader: 'sass-loader',
  options: {
    includePaths: [
      path.resolve('node_modules/xbem/src/')
    ]
  }
}
```
example.scss (your sass file anywhere in the project)
```
@import 'xbem';
```


## Usage
---
### Blocks

* code
```
@include block(menu) {
  // styles here
  color: red;
}
```
* output
```
.menu {
  //styles here
  color: red;
}
```

### Elements

* code
```
@include block(menu) {
  // styles here
  color: red;

  @include element(item) {
    //styles here
    background-color: blue;
  }
}
```
* output
```
.menu {
  //styles here
  color: red;
}

.menu__item {
  //styles here
  background-color: blue;
}
```

### Modifiers

* code
```
@include block(menu) {
  // styles here
  color: red;

  @include element(item) {
    //styles here
    background-color: blue;

    @include modifier(big) {
      font-size: 200%;
    }
  }
}
```
* output
```
.menu {
  //styles here
  color: red;
}

.menu__item {
  //styles here
  background-color: blue;
}

.menu__item, .menu__item--big {
  //styles here
  background-color: blue;
}

.menu__item--big {
  font-size: 200%;
}
```

### States

* code
```
@include block(menu) {
  // styles here
  color: red;

  @include state(isHidden) {
    display: none;
  }
}
```
* output
```
.menu {
  //styles here
  color: red;
}

.menu.\\+isHidden {
  display: none;
}
```
