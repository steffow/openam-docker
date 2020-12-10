# AM Dockerfile


This is designed to be a simple AM image for testing.

If you have an existing configuration store, you can configure AM to use it by creating
an appropriate boot.json file with boot passwords stored in keystore.jceks.

It includes a local Amster install for installing and configuring AM.


# Building

* The Dockerfile assumes that the openam.war and Amster.zip file is pre-downloaded in this directory.

``` 
$ docker build -t am-eval . 
```

followed by

``` 
$ docker run --name am-eval -p 8080:8080 -v $PWD/openam-configuration:/home/forgerock/openam/ am-eval 
```


# Customizing the Web App

If you wish to customize the AM web app, there are two strategies that you can use:

* Inherit FROM this image, and overlay your changes on /usr/local/tomcat/webapps/openam/
* Before you start AM, dynamically copy in the changes. This is the strategy used in the Helm charts. Set
 the CUSTOMIZE_AM variable to the path to a customization script.
