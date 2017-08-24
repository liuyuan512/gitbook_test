#组合的益处
组合仅仅是将简单的函数放在一起产生一个复杂的函数。也就是两个很关键的点
- 简单的函数
- 组合成另一个函数

组件仅仅是由简单的函数构建出来的。下面看一个例子
```js
function getProfileLink (username) {
  return 'https://github.com/' + username
}
```
这是一个很简单的函数，同样下面这个函数也是
```js
function getProfilePic (username) {
  return 'https://github.com/' + username + '.png?size=200'
}
```
这两个函数都是简单函数，那么可以把他们组合进入另一个函数里
```js
function getProfileData (username) {
  return {
    pic: getProfilePic(username),
    link: getProfileLink(username)
  }
}
```
下面是我们不用组合的特性，直接写一个有同样功能的函数
```js
function getProfileData (username) {
  return {
    pic: 'https://github.com/' + username + '.png?size=200',
    link: 'https://github.com/' + username
  }
}
```
技术上讲这没有任何错误，这仅仅是JavaScript代码而已。但是这并不是组和。不用组合的话，这个函数会导致很多潜在的错误。如果其他地方也需要这个用户的GitHub的链接，那么久需要编写重复性的代码了。一个好的函数应该遵循"DOT"规则
>Do One Thing

这个函数做了不止一件事情:它创建了两个不同的URL，把它们作为一个对象的属性作为存储，并且返回这个对象。而上面那个组合的版本每一个函数仅仅只做了一件事情:
- **getProfileLink**-仅仅是创建了一个用户GitHub的个人链接
- **getProfilePic**-仅仅是创建了用户的GitHub的个人图片
- **getProfileData**-返回一个新的对象

#React的组合
React充分利用了组合的特性。React用*组件(coponents)*来创建一系列的UI界面。我们来看一个例子，这里是3个不同的组件
```react
<Page />
<Article />
<Sidebar />
```
现在我们把这些简单的组件组合起来，创造一个复杂一点的组件
```
<Page>
  <Article />
  <Sidebar />
<Page />
```
现在**Page**组件里面又有了一个**Article**和**Sidebar**两个组件。这就类似于之前的例子**getProfileData**函数里面包含 **getProfileLink**函数和**getProfilePic**函数一样
#延伸阅读
- [Compose me That: Function Composition in JavaScript](https://www.linkedin.com/pulse/compose-me-function-composition-javascript-kevin-greene)
- [Functional JavaScript: Function Composition For Every Day Use](https://hackernoon.com/javascript-functional-composition-for-every-day-use-22421ef65a10)