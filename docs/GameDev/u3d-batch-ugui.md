---
layout:    doc
title:    UGUI合批
permalink:    /gamedev/u3d-batch-ugui/
---

# UGUI原理
1. Canvas
2. ReBatch  
当你的Canvas下的一个元素发生变化了，就会重新绘制当前Canvas下的所有的绘制元素，不管其是否变化过。重新计算其图片、位置、缩放、文本等等元素
3. ReBuild  
而Rebuild在ReBatch之后，是每个UI元素自己的操作。比如A元素变了，而B元没有变，那么A元素就自己改一下自己就好了。  
至于哪些元素需要Rebuild，则 Canvas.BuildBatch 里面就计算好了。
4. Other
- 新版的Unity（5.2+）将 Canvas.BuildBatch 放在了其他线程进行操作，而在的手一般都是多核（骁龙650就是6核了），电脑也是，所以动静分离的优化不会帧率造成影响。多的Canvas反而会打断合批，增加DrawCall，其实也是需要取舍。不过即便在别的线程里操作，也是要进行运算的，运算多一些CPU发热手机就会降，这也是很麻烦的事情。
- 不过在测试的时候，如果使用了上千个变化的UI元素和上千个不变的元素进行测，还是能现动静分离的差别的。其实这个原因猜测是用于计算Canvas.BuildBatc的线程耗时已经过了主线程，造成掉帧
- mesh
- 层级深度