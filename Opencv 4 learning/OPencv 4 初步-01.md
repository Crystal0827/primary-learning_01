# 1.读取并展示图片

```c++
void main( ){
    string path;
    Mat img = imread(path);
    imshow("windows_img",img);
}
```



# 2.导入视频

```c++
void main(){
    string path;
    VideoCapture cap(path);
    Mat img;
    while(1){
        cap.read(img);
        imshow("video",img);
        waitKey(20);
    }
}
```

```c++
void main(){
    VideoCapture cap(1);
    Mat img;
    while(1){
        cap.read(img);
        imshow("camera",img);
        waitKey(20);
    }
}
```



# 3.高斯滤波，Canny边缘检测

```c++
void main(){
    string path;
    Mat img = imread(path);
    GaussianBlur（img,imgBlur,Size(3,3),3,0);//要有高斯滤波器尺寸，x轴y轴标准差（调节二维高斯概率分布图像）
    Canny（imgBlur,imgCanny,25,75);//要有两个阈值，区分强边缘和弱边缘；
    imshow("GaussianBlur",imgBlur);
    imshow("Canny",imgCanny);
}
```



# 4.调整图片大小并裁剪

```c++
void main(){
    string path;
    Mat img = imread(path);
    Mat imgResize,imgCrop;
    resize(img,imgResize,Size(30,30));
    Rect roi(200,100,300,300);//绘制矩形，roi指Region of Interest,前两个为矩形左上角坐标，后两个为列和行
    imgCrop = img(roi);
    imshow("Image Resize",imgResize);
    imshow("Image Crop",imgCrop);
}
```



# 5.绘制线条，圆形，矩形

```c++
void main(){
    string path;
    Mat img = imread(path);
    cicle(img,Point(200,100),155,Scalar(255,255,255),FILLED);//要有颜色标量Scalar
    line(img,Point(200,100),Point(233,344),Scalar(0,0,0),2);//可设置线宽，线边缘类型（4邻域，8邻域等）
    Rect roi(200,100,300,300);
    rectangle(img,roi,Scalar(0,0,0),2);//一样有边缘宽度和边缘类型
}
```



# 6.利用颜色进行识别

```c++
void main(){
    string path;
    Mat img,imgHSV,mask;
    Mat img = imread(path);
    cvtColor(img,imgHSV,COLOR_BGR2HSV);
    int hmin,hmax,smin,smax,vmin,vmax;
    nameWindow("Trackbar",(640,200));
    creatTrackbar("H min","Trackbar",&hmin,179);
    creatTrackbar("H max","Trackbar",&hmax,179);
    creatTrackbar("S min","Trackbar",&smin,255);
    creatTrackbar("S max","Trackbar",&smax,255);
    creatTrackbar("V min","Trackbar",&vmin,255);
    creatTrackbar("V max","Trackbar",&vmax,255);
    while(1){
        Scalar lower(hmin,smin,vmin);
        Scalar upper(hmax,smax,vmax);
        inRange(imgHSV,lower,upper,mask);
        imshow("mask",mask);
        imshow("HSV",imgHSV);
        imshow("img",img);
    }
}
```

