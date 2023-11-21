## Assets Checker - [Unity资源检测工具](https://upr.unity.cn/instructions/assetchecker)
`assetcheck.exe generate-config` 生成配置文件 [自定义配置文件页面](https://upr.unity.cn/asset-check-config)  
  
`assetcheck.exe --project=<project_path> --projectId=<project_id>` 检测资源  
example：`assetcheck.exe --project=D:\Darwin Vinci\Learn\Unity Projects\Unity_Optimization_Examples --projectId=548fefd8-3662-4c12-8614-1ed622b6b28e`  
  
### Audio优化建议
**启用Force to Mono**  
如不需要立体声，开启forceMono可以减少内存和磁盘占用，启用此选项，将双声道改为单声道  
**Sample Rate Setting**  
选择Override Sample Rate可更改音频采样频率，移动端推荐22050Hz。  
**Load Type**  
Decompress On Load：建议压缩后音频大小在200k以下时启用  
Compressed In Memory：建议压缩后音频大小在200k以上时启用
Streaming：如果音频为背景音乐等较长较大的文件时，推荐启用此选项，启用流式加载，避免加载时卡顿