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

### 1. Starting RHSSO and JS Console App <a name="deploy-step-1"/>

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

* Open a browser of choice and try to access **Red Hat Single Sign ON*** on the following address with *admin/admin* credentials: http://localhost:8080/auth

* Open a new tab and try to access **JS Console App** on the following address: http://localhost:80

### 2. Create RHSSO Realm <a name="deploy-step-2"/>

* Return to the **Red Hat Single Sign ON** browser tab and place the mouser on the left top corner, right above the *Master*. Click on the arrow button and select **Add Realm**;
* In the *name* textfield use: *demo*
* Click on *Create*

### 3. Create RHSSO Client APP <a name="deploy-step-3"/>

* Click on *Clients* right bellow the *Realm Settings* at the left menu;
* Click on *Create** button on the right corner;
* On the *Client ID* textfield, use: *js-console*
* Inform the *Root URL*: http://localhost
* Click on **Save** button;

### 4. Create RHSSO Roles <a name="deploy-step-4"/>

* Click on **Roles** right bellow the **Client Templates** at the left menu;
* Click on *Add Role* button;
* Inform a *Role Name* (e.g: realm-role) and click on **Save** button afterward;
* Click on **Clients** right bellow the **Realm Settings** at the left menu;
* Select **js-console** and **Roles** afterward;
* Click on **Add Role** button;
* Inform a *Role Name* (e.g: client-role) and afterwards **Save** button;
* Click on **Roles** again;
* Select *Default Roles*
* Select any role available *Available Roles* list and click on **Add Selected**
* In the *Client Roles* select **js-console** and click on **Add Selected**

### 5. Create RHSSO User <a name="deploy-step-5"/>
### 6. Enable SignUp <a name="deploy-step-6"/>
### 7. Change Themes <a name="deploy-step-7"/>
### 8. User Required Actions <a name="deploy-step-8"/>
### 9. Social Login <a name="deploy-step-9"/>
### 10. Two Factor with OTP <a name="deploy-step-10"/>
### 11. End User Account Management <a name="deploy-step-11"/>



## Additional References <a name="additional-references">

- [Red Hat Fuse on Openshift Official Documentation](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.3/html-single/fuse_on_openshift_guide/index)
- [Red Hat Data Grid on Openshift Official Documentation](https://access.redhat.com/documentation/en-us/red_hat_data_grid/7.3/html-single/red_hat_data_grid_for_openshift/index)
- [JBoss JDG Quickstarts](https://github.com/jboss-developer/jboss-jdg-quickstarts/tree/jdg-7.3.x/openshift)
- [Camel Infinispan Component Documentation](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.3/html-single/apache_camel_component_reference/index#infinispan-component)
- [Offload your database data into an in-memory data grid for fast processing made easy](https://developers.redhat.com/blog/2017/04/03/offload-your-database-data-into-an-in-memory-data-grid-for-fast-processing-made-easy/)
