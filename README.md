请先安装opencv & numpy库：pip3 install opencv-python numpy

参数解释

blurred:
这是输入图像，通常是经过高斯模糊处理的灰度图像，以减少噪声和检测假圆。

cv2.HOUGH_GRADIENT:
这是检测方法，目前 OpenCV 仅支持 HOUGH_GRADIENT 方法。

dp:
累加器分辨率与图像分辨率的反比。dp=1.2 表示累加器数组的分辨率是输入图像分辨率的 1.2 倍。较高的 dp 值会降低累加器的分辨率。

minDist:
检测到的圆的圆心之间的最小距离。如果 minDist 太小，多个相邻的圆可能被检测到。如果太大，可能会漏掉一些圆。

param1:
传递给 Canny 边缘检测器的高阈值。低阈值为高阈值的一半。如果图像边缘不明显，可能需要调整这个值。

param2:
累加器阈值，只有累加器中得分高于 param2 的圆心才会被检测为圆。较低的 param2 值会检测到更多的圆，但可能包括一些错误检测的圆。

minRadius:
检测到的圆的最小半径。如果知道圆的大致大小，可以设置这个值以减少检测错误。

maxRadius:
检测到的圆的最大半径。如果知道圆的大致大小，可以设置这个值以减少检测错误。

如何调整这些参数
dp：通常设置为1或更高值（例如1.2）。增大此值可以降低计算复杂度，但可能会影响检测精度。
minDist：需要根据图像中的目标物体的间距进行调整。如果目标物体之间距离较近，可以设置较小值。如果目标物体之间距离较远，可以设置较大值。
param1：可以基于边缘的清晰度进行调整。通常可以保持默认值50，但如果边缘不明显，可以增加或减少此值。
param2：这是最重要的参数之一。值较高会减少检测到的圆，但提高准确性。值较低会增加检测到的圆，但可能会包括错误检测的圆。
minRadius 和 maxRadius：根据目标物体的实际大小进行设置。如果已知目标物体的大小范围，可以设置合适的最小和最大半径值。
