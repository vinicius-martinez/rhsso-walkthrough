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

1. [Starting RHSSO and slide-demo-app](#demo-step-1)
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

### 1. Starting RHSSO and slide-demo-app <a name="deploy-step-1"/>

* Execute *docker pull* to download both **Red Hat Single Sign ON** and **Red Hat Single Sign On JS Console App:**

  * * Pulling **Red Hat Single Sign ON 7.3** and **Red Hat Single Sign On JS Console App:**

    ```
    docker pull viniciusmartinez/rhsso73:1.0
    docker pull viniciusmartinez/sso-console-app:1.0
    ```

### 2. Create RHSSO Realm <a name="deploy-step-2"/>
### 3. Create RHSSO Client APP <a name="deploy-step-3"/>
### 4. Create RHSSO Role <a name="deploy-step-4"/>
### 5. Create RHSSO Realm <a name="deploy-step-5"/>
### 6. Create RHSSO Realm <a name="deploy-step-6"/>
### 7. Create RHSSO Realm <a name="deploy-step-7"/>
### 8. Create RHSSO Realm <a name="deploy-step-8"/>
### 9. Create RHSSO Realm <a name="deploy-step-9"/>
### 10. Create RHSSO Realm <a name="deploy-step-10"/>
### 11. Create RHSSO Realm <a name="deploy-step-11"/>



## Additional References <a name="additional-references">

- [Red Hat Fuse on Openshift Official Documentation](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.3/html-single/fuse_on_openshift_guide/index)
- [Red Hat Data Grid on Openshift Official Documentation](https://access.redhat.com/documentation/en-us/red_hat_data_grid/7.3/html-single/red_hat_data_grid_for_openshift/index)
- [JBoss JDG Quickstarts](https://github.com/jboss-developer/jboss-jdg-quickstarts/tree/jdg-7.3.x/openshift)
- [Camel Infinispan Component Documentation](https://access.redhat.com/documentation/en-us/red_hat_fuse/7.3/html-single/apache_camel_component_reference/index#infinispan-component)
- [Offload your database data into an in-memory data grid for fast processing made easy](https://developers.redhat.com/blog/2017/04/03/offload-your-database-data-into-an-in-memory-data-grid-for-fast-processing-made-easy/)
