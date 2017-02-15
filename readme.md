cppKinect2, a very user-friendly way to use Kinect One with C++

Go to the tutorial: https://github.com/gdubrg/cppKinect2/wiki/cppKinect2-%E2%80%90-Use-Kinect-One-with-C-plus-plus

# cppKinect2
A very **user-friendly** way to use Kinect One with **C++**

***

**Prerequisites:**
- OpenCV
- Microsoft Kinect SDK (v2.0)

***

**How to use:**
* Import all files (.cpp, .h) in your project. _Acquisitionkinect2_ is the acquisition from Microsoft Kinect One, _frameset.h_ is the container for all data extracted from the device.
* Create a loop and call the method `getframe(frameset)`, using as parameter an instance of frameset.h
* Get the data from the frameset
* That's all!

***

**Code sample**
```
int main(){
 ...
 Acquisition *_pkinect = nullptr;
 FrameSet frame;

 _pkinect = new AcquisitionKinect2();
 _pkinect->setSkeleton(MODE_CLOSEST);
 _pkinect->setResolution(RESOLUTION_VGA);

 while(1){
   _pkinect->getFrame(frame);
}
```
***
**Settings**:
* `setSkeleton()`: select which skeleton in the scenario (`MODE_CLOSEST` selects the closest skeleton from device)
* `setResolution()`: select resolution of RGB frame (`RESOLUTION_VGA`, `RESOLUTION_FULLHD`)

***
**Data inside frameset**:
* Kinect version (`int kinectVersion`)
* RGB (`cv::Mat RGB`)
* Depth with skeleton (`cv::Mat depth`)
* Depth without skeleton 3 channels (`cv::Mat depthWithoutSkeleton`)
* Depth without skeleton 1 channels (`cv::Mat depthWithoutSkeleton1ch`)
* Joint Real (`std::vector<tripletPoint> bodyJoint`)
* Joint RGB (`std::vector<tripletPoint> bodyJointRGB`)
* Joint Depth (`std::vector<tripletPoint> bodyJointDepth`)
* Head Pitch (`int pitch`)
* Head Roll (`int roll`)
* Head Yaw (`int yaw`)

***

**Skeleton Joint names:**
```
enum jointNames{
    FS_head,
    FS_neck,
    FS_shoulderCenter,
    FS_spineShoulder,
    FS_shoulderRight,
    FS_elbowRight,
    FS_wristRight,
    FS_handRight,
    FS_thumbRight,
    FS_shoulderLeft,
    FS_elbowLeft,
    FS_wristLeft,
    FS_handLeft,
    FS_thumbLeft,
    FS_spineMid,
    FS_spine,
    FS_spineBase,
    FS_hipCenter,
    FS_hipRight,
    FS_kneeRight,
    FS_ankleRight,
    FS_footRight,
    FS_hipLeft,
    FS_kneeLeft,
    FS_ankleLeft,
    FS_footLeft,
    FS_handTipRight,
    FS_handTipLeft
};
```

