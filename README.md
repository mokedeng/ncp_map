# ncp_map

## 《Vue实战开发百度实时大数据疫情地图》

效果图如下：
![](https://timegods.oss-cn-shenzhen.aliyuncs.com/markdown/yqmap.jpg)

用vue的脚手架搭建框架
```
vue create ncp_map
```

安装依赖
```
npm install axios jsonp
```

疫情数据来源于新浪的接口，是jsonp接口，不是axios。接口地址：
```
https://interface.sina.cn/news/wap/fymap2020_data.d.json?_=1580892522427
```

没有做定时刷新，为啥呢，因为我懒，加个定时器就行了

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
