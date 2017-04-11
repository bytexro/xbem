# B.E.M FRAMEWORK

[![Bytex](http://i.imgur.com/HZ1NEBA.png)](http://bytex.ro/)

### by Prisecaru Bogdan


## Why should we use this?
---
- Easy and intuitive mixins for writing [B.E.M](https://en.bem.info/methodology/) classes
- Optimized output CSS
- No need for more then one class per element (except *+state* classes)
- No nesting beyond level one (except *+state* classes)


## Installation
---

In your terminal:
```
npm install --save xbem
```
or
```
npm install -S xbem
```
In your webpack project, use 'sass-loader' with the following option:

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
Webpack will resolve your import to *"node_modules/xbem/src/xbem"*

#
## Usage
---
### Blocks

code
```
@include block(humanbody) { // styles here
 position: relative;
}
```
output
```
.humanbody {
  position: relative;
}
```

### Elements

code
```
@include block(humanbody) { // styles here
  position: relative;

  @include element(hand) {
    height: 100px;
  }
  @include element(foot) {
    height: 200px;
  }
}
```
output
```
.humanbody {
  position: relative;
}
.humanbody__hand {
  height: 100px;
}
.humanbody__foot {
  height: 200px;
}

```

### Modifiers

code
```
@include block(humanbody) { // styles here
  position: relative;

  @include element(hand) {
    height: 100px;

    @include modifier(left) {
      left: 0;
    }
  }
  @include element(foot) {
    height: 200px;

    @include modifier(right) {
      right: 0;
    }
  }
}
```
output
```
.humanbody {
  position: relative;
}
.humanbody__hand--left, .humanbody__hand {
  height: 100px;
}
.humanbody__hand--left {
  left: 0;
}
.humanbody__foot--right, .humanbody__foot {
  height: 200px;
}
.humanbody__foot--right {
  right: 0;
}
```

### States

code
```
@include block(humanbody) { // styles here
  position: relative;

  @include state(issick) {
    float: left;
  }
}
```
output
```
.humanbody {
  position: relative;
}
.\+issick.humanbody {
  float: left;
}
```
#
## A More Complex Example
#
code
```
@include block(humanbody) { // styles here
  position: relative;

  @include element(hand) {
    height: 100px;

    @include modifier(left) {
      left: 0;
    }
  }
  @include element(foot) {
    height: 200px;

    @include modifier(right) {
      right: 0;
    }
  }

  @include state(issick) {
    float: left;

    @include element(hand) {
      color: green;

      @include modifier(left) {
        overflow: hidden;
      }
    }

    @include element(foot) {
      color: green;

      @include state(isbroken) {
        display: flex;
      }
    }
  }
}
```

output
```
.humanbody {
  position: relative;
}
.humanbody__hand--left, .humanbody__hand, .\+issick .humanbody__hand, .\+issick .humanbody__hand--left {
  height: 100px;
}
.humanbody__hand--left {
  left: 0;
}
.humanbody__foot--right, .humanbody__foot, .\+issick .humanbody__foot {
  height: 200px;
}
.humanbody__foot--right {
  right: 0;
}
.\+issick.humanbody {
  float: left;
}
.\+issick .humanbody__hand {
  color: green;
}
.\+issick .humanbody__hand--left {
  overflow: hidden;
}
.\+issick .humanbody__foot {
  color: green;
}
.\+issick .humanbody__foot.\+isbroken {
  display: flex;
}
```
#
### Mixins
> Not part of the B.E.M methodology
> Just some usefull mixins to use in your SASS projects


| Mixin | Codepen Link |
| ------ | ------ |
| flexgroupof | http://codepen.io/bogdan_bytex/pen/BWKWXa |
