# NGR.ImageOverlay
用来在地图上的特定区域内显示一张图片，该类实现了`ILayer`接口。

##用法用例
```javascript
var img = "path/to/image.png",
    bounds = [[31, 121], [32, 122]];
    
NGR.imageOverlay(img, bounds).addTo(map);
```

## 创建方法
| 创建方法 | 描述 |
| -- | -- |
| `NGR.ImageOverLay( <String> imageUrl, <LatLngBounds> bounds, <ImageOverlay options> options? )` | 通过给定的图片URL、地理范围和选项实例化一个图片浮层。 |


## 选项
| 选项 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| `opacity` | `Number` | `1.0` | 图片浮层的透明度 |

## 方法
| 方法 | 返回值 | 描述 |
| -- | -- | -- |
| `addTo( <Map> map )` | `this` | 向地图中添加图片浮层 |
| `setOpacity( <Number> opacity )` | `this` | 设置图片浮层的透明度 |
| `setUrl( <String> imageUrl )` | `this` | 更改浮层内容图片的URL |
| `bringToFront()` | `this` | 将该层置于所有层的顶部 |
| `bringToBack()` | `this` | 将该层置于所有层的底部 |

