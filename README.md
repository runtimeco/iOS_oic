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

#### Discovery
To discover OIC enabled devices, hit the discovery button in the top right corner of the Main screen. This will discover devices using the options given to the OCDoResource. By default, we will do a general discovery of all OIC enabled devices over BLE and IP transport. Any resource containing a valid Mynewt sensor framework resource type will be added to the Sensors list while any other device will be added to the Smart Devices list

#### Observing a Sensor 
To Observe a sensor, click the sensor in the list. This will bring up the sensor screen which will immediately start observing the sensor. You can stop/start observing the sensor by hitting the start/stop observe button in the top right of the navigation bar. 
![alt text](https://github.com/runtimeco/iOS_oic/blob/master/photos/sensor_img.jpg)

### Useful Files
#### iotivity_itf.h and iotivity_itf.m
The `iotivity_itf.h` is the header file for the functions used for the communication between the iOS device and the sensors. The `iotivity_itf.m` contains the functions used for discovering resources, getting values from resources, observing resource values and setting resource values.

#### Peripheral.h and Peripheral.m
The `Peripheral.h` is the header file which declares the properties a discovered Peripheral can contain. `Peripheral.m` has the function to add the resources in the Peripheral Resource array.

#### A few functions involved
##### Discovery of IP and BLE resources
```
// BLE discover resources
/*
* @param delegate : reference to the class that called the function
* @param address  : uuid of the device 
*/
- (int) discover_allDevices: (id) delegate andAddress : (NSString *)address

// IP discover resources
/*
* @param delegate : reference to the class that called the function
*/
- (int) discovery_start:(id)delegate
```
##### Get resource values
```
// Get resource values
/*
* @param delegate : reference to the class that called the function
* @param uri : resource uri
* @param devAddr : device address and related details
*/
- (int) get_generic:(id)delegate andURI:(NSString *)uri andDevAddr:(OCDevAddr) devAddr
```
##### Set resource values
```
// Set resource values
/*
* @param delegate : reference to the class that called the function
* @param uri : resource uri
* @param devAddr : device address and related details
* @param payload : set resource values packaged in OCRepPayload
*/
- (int) set_generic:(id)delegate andURI:(NSString *)uri andDevAddr:(OCDevAddr)devAddr andPayLoad:(OCRepPayload *) payload{
```
##### Observe resource values
```
// Observe resource values
/*
* @param delegate : reference to the class that called the function
* @param uri : resource uri
* @param devAddr : device address and related details
*/
- (int) observe_light:(id)delegate andURI:(NSString *)uri andDevAddr:(OCDevAddr)devAddr
```
##### Cancel Observe
```
// Cancel the resource value observation
/*
* @param delegate : reference to the class that called the function
* @param uri : resource uri
* @param devAddr : device address and related details
* @param handle : OCDoHandle returned from the observe API call
*/
- (int) cancel_observer:(id)delegate andURI:(NSString *)uri andDevAddr:(OCDevAddr)devAddr andHandle:(OCDoHandle)handle
```
