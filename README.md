# little_one_drive_app

### Basic Overview 

#### A simple ionic + cordova app which builds on [little_list](https://github.com/AliceDigitalLabs/little_list).

Little OneDrive is a *JAM Stack* application created to demonstrate how Ionic V1 and Cordova can be used to create a cross - platform mobile app and how OneDrive authentication can be achieved on a mobile device.

Little OneDrive works as a cross-platform mobile application that connects to the OneDive API.

Little OneDrive lets you do two things:

1. Request a OneDrive **access token**.
2. Download a specific file from a OneDrive account.

### Requirements

- IDE (Preferably [Visual Studio Code](https://code.visualstudio.com/))
- [Node.js](<https://nodejs.org/en/about/>)
- [NPM](<https://docs.npmjs.com/about-npm/>)
- [Microsoft Azure Developer](https://azure.microsoft.com/en-gb/free/search/?&ef_id=CjwKCAiAhJTyBRAvEiwAln2qB-WVYSkGIon6ikH8ZgsDn1uIR851vKd7zm_q6RWwNkUW-Yt1A_BKJBoCj8oQAvD_BwE:G:s&OCID=AID2000125_SEM_ZzxoRbwK&MarinID=ZzxoRbwK_324561472948_%2Bazure%20%2Bmicrosoft_b_c__64529419638_aud-394034018570:kwd-22984673891&lnkd=Google_Azure_Brand&dclid=CjkKEQiAhJTyBRDctv2Dn-qtyNQBEiQA6ar91DjWJgfEuuh2o6KGldyhkHQo2ghYSXWAdEOuvCNDnkfw_wcB) (For Client ID and Log In)
- [Ionic](<https://ionicframework.com/docs/v1/>)
- [Gradle](<https://gradle.org/install/>)
- [Android Studio](<https://developer.android.com/studio>)



### Getting Started

#### Creating Developer Account and Registering Application

1. Navigate to [Microsoft Azure](https://azure.microsoft.com/en-gb/free/search/?&ef_id=CjwKCAiAhJTyBRAvEiwAln2qB-WVYSkGIon6ikH8ZgsDn1uIR851vKd7zm_q6RWwNkUW-Yt1A_BKJBoCj8oQAvD_BwE:G:s&OCID=AID2000125_SEM_ZzxoRbwK&MarinID=ZzxoRbwK_324561472948_%2Bazure%20%2Bmicrosoft_b_c__64529419638_aud-394034018570:kwd-22984673891&lnkd=Google_Azure_Brand&dclid=CjkKEQiAhJTyBRDctv2Dn-qtyNQBEiQA6ar91DjWJgfEuuh2o6KGldyhkHQo2ghYSXWAdEOuvCNDnkfw_wcB) and create a free account.
2. It will ask for your details notably; *phone number* and *card details*. This is only for verification - **you will not be charged** **unless** - you buy/upgrade to premium membership earlier on or after 12 month time span has expired.
3. Navigate to [Microsoft Azure Portal](<https://portal.azure.com/#home>).
4. After navigating to the portal you search for App Registrations. Once there, click the button '**New registration**' then name the application. 
5. Choose what type of accounts you would like to allow to authenticate for example allow organisation only emails such as <u>@stu.mmu.ac.uk</u>, <u>@ad.mmu.ac.uk</u> or personal emails such as <u>@live.com</u>, <u>@outlook.com</u> and <u>@hotmail.com</u> among others.
6. It will also ask for a Redirect URI,  This is used to return users to specific pages within your application after validating their ID, an example of an application callback is 'http://localhost/callback.html'.



#### Filling in Registered Application Details

Now that we have registered your app with the Microsoft API we need to fill in some gaps so our app knows what to ask the API for.

1. Take note of the **Application ID** (also known as Client ID).

2. Click the **'authentication'** button found in the side menu.

3. Click the a *'Add a platform'* button then Choose the *'Web Option'*. 

4. Add your RedirectURI again. Ignore the logout URL unless you have one.

5. Under *'Implicit Flow'* check the box next to access token then configure. Now near the end of the page under 'Advance settings' click **yes** to treat as a public client.

6. Now go to the *'API permissions'* button and remove the default permission given by Microsoft Graph.

7. Now click Add a permission > Microsoft Graph > Delegated permissions > check Sites.Read.All > Add permissions. 

8. Finally click the button Manifest in the side menu this will reveal a JSON type file.

9. Look for 'oauth2AllowImplicitFlow' it will be false by default change this to 'true' then click the 'Save' button above.

   What is a [Client ID?](<https://www.oauth.com/oauth2-servers/client-registration/client-id-secret/>		)

Differences between [Delegated and Application Permissions.](<https://massivescale.com/application-vs-delegated-scopes/>)

#### Filling in Client Details 

Within the credentials.service.js file locate `service` on Line 16. Modify `service` to the appropriate details, these details must match with the application details filled out earlier.

`clientId` : Application Id

`redirectUri` : Application redirect URL

`scopes`: Application scopes delimited by a space and formatted to lowercase (example Sites.Read.All => sites.read.all)

`authServiceUri`: Don't change as it needs to be - <https://login.microsoftonline.com/common/oauth2/v2.0/authorize>

Your credential.service.js file will look near identical this, with the only possible differences being your Client ID and RedirectURI

```javascript
            clientId: "7107aae1-8e0f-4063-8202-0e9a22d708af",
            redirectShort: "http://localhost/callback",
            redirectUri: "http://localhost/callback.html",
            scopes: "sites.read.all",
            authServiceUri: "https://login.microsoftonline.com/common/oauth2/v2.0/authorize"
```



### Deployment

As Android and iOS are two different operating systems their means of deployment do differ somewhat and branch off into their way of doing things however the first few steps remain mostly the same.

### Deployment on Android

For Android deployment see [little_list](<https://github.com/AliceDigitalLabs/little_list/blob/master/README.md>)

### Deployment on iOS

**Creating An Apple Developer Account (Deploying on iOS Devices)**

Before deploying on iOS it is imperative, to create an Apple Developer Account as deployment is not available until an Apple Team ID has been assigned to the details of the app. The following link will bring you to the account creation page: https://appleid.apple.com/account?appId=632&returnUrl=https%3A%2F%2Fdeveloper.apple.com%2Fenroll%2F#!&page=create

1. Once you have `ionic -v` working, input the command `ionic cordova platform add ios`
2. Now if you look in the file directory you will see a platforms folder open that folder to find a folder named 'ios'.
3. Next step is to boot up Xcode.
4. Now open the 'ios' folder, in Xcode.
5. Click the top file this usually identified as the project name.
6. You will a see a section titled 'Signing' within this you will find the phrase 'Team' with 'None' defaulted in the input. Add your team here - this will be classed as a signature.
7. After that has finished installing, run this command `ionic cordova run ios` to install and launch on your iPhone.
8. You might recieve a complaint from the console telling you the application has not been launched this is because your phone does not recognise your developer profile, how ever the app itself has been downloaded to your device.
9. Not being able to open it due to the operating system seeing you as an untrusted developer. We need to change that.
10. To make your phone recognise your developer profile go to your Settings > General > Device Management > Your App > Press Trust App
11. Now if you go back to your home screen you will find your app, ready for use!

### License

This project is licensed under the MIT License - see the [LICENSE.md](https://gist.github.com/PurpleBooth/LICENSE.md) file for details