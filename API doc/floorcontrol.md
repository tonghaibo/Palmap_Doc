# NGR.Control.Floor
基本的楼层切换控件，继承自`NGR.Control`。默认会放置于地图的右下角。

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.control.floor( <Floor control options> options? )` | 根据给定的选项创建一个楼层切换控件 |

## 简单用例
```javascript
var control = NGR.control.floor({ position: "bottomLeft" });
control.setFloorList(['F1', 'F2', 'F3', 'F4']);
control.setCurrentFloor('F3');
control.on('floorChange', function(e) {
    console.log("Switch floor from: ", e.from, "to: ", e.to);
});
```

## 属性
| 属性 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `position` | `String` | `bottomright` | 控件在地图上的位置，参见`NGR.Control`的文档获取更多信息 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `enable()` | `this` | 从楼层选择器的HTML元素中移除`disabled`属性 |
| `disable()` | `this` | 向楼层选择器的HTML元素中添加属性`disabled`，SDK自带一个禁用效果，可以通过CSS重新定义这个效果 |
| `setFloorList( <String[]> floors )` | `this` | 为楼层选择器设置所有可用楼层 |
| `getCurrentFloor()` | `String` | 返回当前所在的楼层 |
| `setCurrentFloor( String floor )` | `this` | 设置当前活动的楼层，楼层必须是`setFloorList`函数参数中的一个元素 |

## 事件
您可以通过这些方法来订阅下列事件。

| 事件 | 数据类型 | 描述 |
| -- | -- | -- |
| `floorChange` | `Event` | 当用户点击楼层按钮切换楼层时触发，您可以访问事件的`from`和`to`属性获取之前楼层和目标楼层 |
