#B.E.M Framework

##Why should we use this?
- No need for more then 1(one) class per element (except +state classes)
- No nesting beyond level 1(one) (except +state classes)
- Optimized output CSS
- Easy and intuitive mixins for writing BEM classes

##Usage

###Blocks

```
@include block(menu) {
  // styles here
  color: red;
}

```
#### output

```
.menu {
  //styles here
  color: red;
}

```
###Elements

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
#### output

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

###Modifiers

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
#### output

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

###States

```
@include block(menu) {
  // styles here
  color: red;

  @include state(isHidden) {
    display: none;
  }
}

```
#### output

```
.menu {
  //styles here
  color: red;
}

.menu.\\+isHidden {
  display: none;
}

```
