## Assets Checker - [Unity资源检测工具](https://upr.unity.cn/instructions/assetchecker)
`assetcheck.exe generate-config` 生成配置文件 [自定义配置文件页面](https://upr.unity.cn/asset-check-config)  
  
`assetcheck.exe --project=<project_path> --projectId=<project_id>` 检测资源  
example：  
`assetcheck.exe --project=D:\Darwin Vinci\Learn\Unity Projects\Unity_Optimization_Examples --projectId=548fefd8-3662-4c12-8614-1ed622b6b28e`  
  
## 资源优化
### Audio 优化
**Force to Mono**  
如不需要立体声，开启Force to Mono可以减少内存和磁盘占用，启用此选项，将双声道改为单声道  
**Sample Rate Setting**  
选择Override Sample Rate可更改音频采样频率，移动端推荐22050Hz  
**Load Type**  
Decompress On Load：建议压缩后音频大小在200k以下时启用  
Compressed In Memory：建议压缩后音频大小在200k以上时启用
Streaming：如果音频为背景音乐等较长较大的文件时，推荐启用此选项，启用流式加载，避免加载时卡顿，但有额外的CPU开销

### Model 优化  
Unity中三种Mesh优化：  
Player Settings中的**Vertex Compression**、**Optimize Mesh Data**  
Mode Impoter中的**Mesh Compression**，Mesh Compression压缩以节省硬盘空间，但不会节省Runtime内存  
- 开启Dynamic Batching后，顶点数300一下的模型Vertex Compression不生效
- Model Importer中开启Read/Write Enable后，Vertex Compression不生效
- Model Importer中开启Mesh Compression后，Vertex Compression、Optimize Mesh Data不生效

### Animation 优化
Animation Clip的信息：
```
Curves Pos: 0 Quaternion: 0 Euler: 1 Scale: 0 Muscles: 0 Generic: 0 PPtr: 0Curves Total: 3,Constant: 0 (0.0%) Dense: 0(0.0%) Stream: 3(100.0%)2.7 KB
```
Model Impoter中的Animation标签下的三个Error数值越大，Constant也会相应的越多，Constant占比越大，代表动画播放的性能越好  
> ···Error属性代表的是Transform的误差，默认为0.5，代表5/1000的误差，如两帧之间的差别只有5/1000，则认为两帧相同，例如1米的误差为5毫米，1000米的误差为5米，会影响在动画的表现细节及精度。