# NGR.Point
本类代表一个以像素为单位的在x,y坐标系上的点。


## 简单用例
```javascript
var point = NGR.point(200, 300);
```
在SDK中大部分接受`NGR.Point`的地方都接受其的数组简化形式，所以下面的代码是等价的：
```javascript
map.panBy([200, 300]);
map.panBy(NGR.point(200, 300));
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.Point( <Number> x, <Number> y )` | 通过给定的`x`坐标和`y`坐标创建一个点对象 |


## 属性
| 属性 | 类型 | 描述 |
| -- | -- | -- |
| `x` | `Number` | `x`坐标的值 |
| `y` | `Number` | `y`坐标的值 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `add( <Point> otherPoint )` | `NGR.Point` | 返回当前点与给定点数值相加后产生的新点 |
| `subtract( <Point> otherPoint )` | `NGR.Point` | 返回当前点与给定点数值做差后产生的新点 |
| `multiplyBy( <Number> number )` | `NGR.Point` | 返回当前点与给定数值相乘后产生的新点 |
| `divideBy( <NUmber> number )` | `NGR.Point` | 返回当前的点除以给定数值后产生的新点 |
| `distanceTo( <Point> otherPoint )` | `Number` | 返回两个点之间的距离 |
| `clone()` | `NGR.Point` | 返回一个当前点的拷贝 |
| `equals( <Point> otherPoint )` | `Boolean` | 当两个点位置一样时，返回`true` |
| `toString()` | `String` | 返回以字符形式表示的点 |
