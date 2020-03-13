# Red Hat Single Sign On Walkthrough

## Description

This demo showcase a step-by-step guide covering basic capabilities from [Red Hat Single Sign ON](https://access.redhat.com/products/red-hat-single-sign-on).

## Building from Source

Source code artifacts are available on *source* directory. No need to build/compile anything, since we're using *JavaScript* and *HTML*.

Docker assets are available on *docker* directory. In order to modify those images, just change *Dockerfile-js-console* or *Dockerfile-rhsso-73* as needed and execute a *docker build -t* from *root* directory . Example:

  ```
  docker build -t rhsso-js-console-app:1.0 -f docker/Dockerfile-js-console .
  docker build -t rhsso73:1.0 -f docker/Dockerfile-rhsso-73 .
  ```

## Demo Script

1. [Starting RHSSO and JS Console App](#demo-step-1)
2. [Create RHSSO Realm](#demo-step-2)
3. [Create RHSSO Client APP](#demo-step-3)
4. [Create RHSSO Roles](#demo-step-4)
5. [Create RHSSO User](#demo-step-5)
6. [Enable SignUp](#demo-step-6)
7. [Change Themes](#demo-step-7)
8. [User Required Actions](#demo-step-8)
9. [Social Login](#demo-step-9)
10. [Two Factor with OTP](#demo-step-10)
11. [End User Account Management](#demo-step-11)

### 1. Starting RHSSO and JS Console App <a name="demo-step-1"/>

* Execute *docker pull* to download both **Red Hat Single Sign ON** and **JS Console App:**
  ```
  docker pull viniciusmartinez/rhsso73:1.0
  docker pull viniciusmartinez/sso-console-app:1.0
  ```
* Bootstrap both both **Red Hat Single Sign ON** and **JS Console App:**

  ```
  docker run -it -p 8080:8080 viniciusmartinez/rhsso73:1.0
  docker run -it -p 80:80 viniciusmartinez/sso-console-app:1.0
  ```
  * if you modify **Red Hat Single Sign ON** default port don't forget to update *keycloak.json;*
* Open a browser of choice and try to access **Red Hat Single Sign ON** on the following address with *admin/admin* credentials: http://localhost:8080/auth
* Open a new tab and try to access **JS Console App** on the following address: http://localhost:80

### 2. Create RHSSO Realm <a name="demo-step-2"/>

* Return to the **Red Hat Single Sign ON** browser tab and place the mouser on the left top corner, right above the *Master*. Click on the arrow button and select **Add Realm**;
* In the *name* textfield use: *demo*;
* Click on *Create*;

### 3. Create RHSSO Client APP <a name="demo-step-3"/>

* Click on *Clients* right bellow the *Realm Settings* at the left menu;
* Click on *Create* button on the right corner;
* On the *Client ID* textfield, use: *js-console;*
* Inform the *Root URL*: http://localhost
* Click on **Save** button;

### 4. Create RHSSO Roles <a name="demo-step-4"/>

* Click on **Roles** right bellow the **Client Templates** at the left menu;
* Click on *Add Role* button;
* Inform a *Role Name* (e.g: realm-role) and click on **Save** button afterward;
* Click on **Clients** right bellow the **Realm Settings** at the left menu;
* Select **js-console** and **Roles** afterward;
* Click on **Add Role** button;
* Inform a *Role Name* (e.g: client-role) and afterwards **Save** button;
* Click on **Roles** again;
* Select *Default Roles;*
* Select any role available *Available Roles* list and click on **Add Selected;**
* In the *Client Roles* select **js-console** and click on **Add Selected;**

### 5. Create RHSSO User <a name="demo-step-5"/>

* Click on **Users** right bellow the **Groups** at the left menu;
* Click on *Add User* button;
* Inform a *Username* and click on **Save** button;
* Got to *Credentials* tab and inform a new password;
* Change *Temporary* to **OFF**;
* Finally click on **Reset Password**;
* Switch back to **JS Console App (http://localhost:80)** and click on **Login**
* The **Red Hat Single Sign ON** login page will be displayed. Inform the credentials from the user you've created on previous step;
* If everything is properly configured, after a successfully login you will be redirected to the **JS Console App**. Please notice the **Init Success (Authenticated)** right below the *Result* label;
  * considering exploring all buttons (Get Profile, Get User Info, Show Token) to familiarize yourself with *OpenID/OAuth* standards;

### 6. Enable SignUp <a name="demo-step-6"/>

* Go back to **JS Console App (http://localhost:80)** and click on **Logout**
* Switch back to **Red Hat Single Sign ON (http://localhost:8080)** and click on **Realm Settings** right bellow the **Realm Name (Demo)** and select *Login;*
* Enable *User Registration*
* Click on **Save**
* On **JS Console App (http://localhost:80)** click on **Login** button;
* Click on **Register** and create a new user informing all required fields;
* * if you experience session issues with other users, considering open a new browser instance or an incognito tab;

### 7. Change Themes <a name="demo-step-7"/>

* On **JS Console App (http://localhost:80)** and click on **Logout;**
* On **Red Hat Single Sign ON (http://localhost:8080)**, click **Realm Settings** and select **Themes** tab;
* Select a different theme from **Login Theme** dropdown list;
* Click on **Save;**
* Go back to **JS Console App (http://localhost:80)** and click on **Login;**
* Notice  a different look'n'feel from **Red Hat Single Sign ON** login page;

### 8. User Required Actions <a name="demo-step-8"/>

* Click on **Users** right bellow the **Groups** at the left menu;
* Click on *View all users* button and select one;
* Select an user by clicking on *Edit*;
* Select a few actions on **Required User Actions** menu;
* Click on **Save**
* Try to login with this user and now you'll have to execute the *Required Actions* previously configured;

### 9. Social Login <a name="demo-step-9"/>

* On **JS Console App (http://localhost:80)** and click on **Logout;**
* Click on **Identity Providers** right bellow the **Roles** at the left menu;
* Select *Github*;
* Open a new tab and access your *Github* account.
  * * Select **Settings** -> **Developer Settings** -> **OAuth App** and finally click on: **New OAuth App**
* Inform an *Application name* and a *Homepage URL* and finally copy the *Redirect URI* from **Red Hat Single Sign ON** and paste it on **CallBack URL**
* Click on **Register Application**
* Copy both **Client ID** and **Client Secret** from *Github* and paste them on *RHSSO*
* Click on **Save**
* Go back to **JS Console App (http://localhost:80)** and click on **Login;**
* Notice that now you have the option to login with *Github*;

### 10. Two Factor with OTP <a name="demo-step-10"/>

* On **JS Console App (http://localhost:80)** and click on **Logout;**
* Click on **Authentication** right bellow the **User Federation** at the left menu;
* Change the default *OTP FORM* from **OPTIONAL** to **REQUIRED**;
* Go back to **JS Console App (http://localhost:80)** and click on **Login;**
* * considering installing *FreeOTP* or *Google Authenticator* and configure the authentication by scanning the provided *QR Code*;


### 11. End User Account Management <a name="demo-step-11"/>



## Additional References <a name="additional-references">
