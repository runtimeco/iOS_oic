# IOS OIC
## Setting up the iOS sensors app with OIC
1. To set up build environment, first run ./setup.sh
2. Ensure you have Cocoapods installed. If you need to install cocoapods execute : *$ sudo gem install cocoapods*
3. To check if you have cocoapods, execute : *$ pod --version*
4. Once you have cocoapods, execute : $ pod install in your project directory.
5. Open your project in Xcode using the **.xcworkspace** (on your terminal in the project directory : *$ open YOUR_PROJECT_NAME.xcworkspace).*
6. Click on the project file. Choose your **target**. In the General tab, go to **Linked Frameworks and Libraries section**, click on **+** and add Charts.framework if not already added.

Clean the project, build and run. (The option to clean, build and run the project will be seen in the Menu Bar -> Product)

## OIC and Iotivity Overview
For more information on OIC and Iotivity for iOS, refer to ```https://github.com/runtimeco/ios_oic_developer/blob/master/README.md```

## MyNewt Sensor Application Overview
The Mynewt Sensor application is a sample for developers looking to use OIC to communicate with Mynewt devices which use the sensor framework to expose sensor data. The source code is available on [github](https://github.com/runtimeco/ios_oic) as a part of runtimeco.

### Understanding the MyNewt Sensor App in iOS
![alt text](https://github.com/runtimeco/iOS_oic/blob/master/photos/sensor_img.jpg)
