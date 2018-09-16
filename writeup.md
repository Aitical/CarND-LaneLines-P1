# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. 建立pipeline
1. 将图像转化成灰度图
2. 进行高斯平滑
3. 获取canny边缘检测结果
4. 指定目标区域的顶点
5. 使用hough变换并画线
  其中在draw_line()函数中,将原来的直接画线修改了一下实现可以整体画出一道直线,思路如下:
  默认至多两条行车线且一条斜率为正一条为负数
  遍历返回的线段,获取最小的y值,同时计算出每条线段对应直线的斜率与截距并保存到对应的数组
  遍历结束后增大y_min,也就是将顶点下移,防止线段交叉
  对于正斜率和负数斜率的线段集合,如果存在的话,使用均值计算出斜率和截距
  设置y_max为图像高度,计算出对应的x值
  画图即可


### 2. 缺陷

1. 无法拟合弯道(曲线)情况
2. 区域选择时区域分划分相对单一,不能拟合到更多更复杂的情况
3. 图像要素相对简单,不能处理有复杂干扰情况


### 3. 改进的建议

1. 尝试选用更好的方法拟合曲线的情况
2. 尝试使用一些深度学习方法,让区域选择可以自动且准确