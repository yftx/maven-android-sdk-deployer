Maven Android SDK Deployer
--------------------------

*only install compatibility lib*
------------------

Author and Project Maintainer including numerous fixes and changes:

Manfred Moser manfred@simpligility.com  at [simpligility technologies inc](http://www.simpligility.com)

Contributors:

- Hugo Josefson <hugo@josefson.org> - properties plugin usage
- Jake Wharton <jakewharton@gmail.com> - 3.2, compatibility v13 and 4.0.3 support
- https://github.com/holdensmagicalunicorn - spelling fix
- Guto Maia <guto@guto.net>- initial USB add on support
- Lorenzo Villani - initial 4.0 support
- Paul Merlin http://eskatos.github.com - Google Analytics extra
- Matteo Panella <morpheus@level28.org> - Google AdMobs extra, support for 4.1
- Benoit Billington https://github.com/Shusshu Google Cloud Messaging Client and Server, annotations.jar, 4.2, APK Expansion, Licensing
- Michael Lake https://github.com/mlake support for Javadoc attachment for platforms
- Nic Strong http://www.codepoets.co.nz Google Play Services (gms)
- Matias Dumrauf http://github.com/mdumrauf - compatibility v7 library support
- https://github.com/skyisle minor documentation fix                            
- Viacheslav Rodionov https://github.com/bepcyc AdbMob update
- David Venable https://github.com/dlvenable admob update
- Jenny Loomis Williamson https://github.com/jloomis fix for deployment
- James Wald https://github.com/jameswald configured groupId and artifactId for support libraries
- Thomas Prochazka https://github.com/tprochazka javadoc attachment

The Maven Android SDK Deployer is a helper maven project that can be
used to install the libraries necessary to build Android applications
with Maven and the Android Maven Plugin directly from your local
Android SDK installation.

ATTENTION!  Currently some android.jar artifacts are available in
Maven central and unless you use maps or usb related dependencies,
android 3.0+, the compatibility library jar files or insist on using
the original jar files from the local SDK install, you might not need
this tool anymore.

You will however need this tool to access the latest Android 4.1
release or to work around bugs like missing JSON libraries in some
older artifacts deployed to Maven central. If you use this tool make
sure your dependencies are as documented here.

The android.jar artifacts in Maven central are available with the
groupId com.google.android, whereas this tool uses android.android to
avoid overlap.

How to Use
----------

Download the latest Android SDK from
http://developer.android.com/sdk/index.html following the instructions
there.
 
- For the default usage of the deployer install **all platforms and
add-on apis**, ensure that all folder in the platforms folder have
names like android-3, android-4 and so on.  

- If you find names using the platform version (e.g. 15) in the folder
name reinstall that platform from the android tool.

- In a similar manner the folder names in add-ons have to use the
pattern addon_google_apis_google-3 up to addon_google_apis_google-15.

- If the folder names are different reinstall the add-ons as well

Set up the environment variable ANDROID_HOME to contain the absolute
 folder you just installed the SDK to (e.g. under bash: export
 ANDROID_HOME=/opt/android_sdk_linux) and ensure that the folder for
 ANDROID_HOME and all files within are readable by the current user

Run the command

    mvn install

in the root folder of this project (same as README you are just
reading) to install all platforms and add-on apis

To install only a certain sdk level use

    mvn install -P 1.5
    mvn install -P 1.6
    mvn install -P 2.1
    mvn install -P 2.2
    mvn install -P 2.3.3
    mvn install -P 3.0
    mvn install -P 3.1
    mvn install -P 3.2
    mvn install -P 4.0
    mvn install -P 4.0.3
    mvn install -P 4.1
    mvn install -P 4.2

As a result you should find the android.jar and maps.jar and a number of other
libraries in your users local repository (~/.m2/repository/) and you can therefore
use the following dependencies in your project

For the core platforms

```xml
<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>1.5_r4</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>1.6_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>2.1_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>2.2_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>2.3.3_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>3.0_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>3.1_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>3.2_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>4.0_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>4.0.3_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>4.1.2_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android</groupId>
  <artifactId>android</artifactId>
  <version>4.2_r1</version>
  <scope>provided</scope>
</dependency>
```

For the maps add ons

```xml
<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>3_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>4_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>7_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>8_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>10_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>11_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>12_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>13_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>14_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>15_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>16_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.google.android.maps</groupId>
  <artifactId>maps</artifactId>
  <version>17_r1</version>
  <scope>provided</scope>
</dependency>
```

For the usb add on

```xml
<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>10_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>12_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>13_r1</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>14_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>15_r2</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>16_r3</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>com.android.future</groupId>
  <artifactId>usb</artifactId>
  <version>17_r2</version>
  <scope>provided</scope>
</dependency>
```

For the compatibility extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>android.support</groupId>
  <artifactId>compatibility-v4</artifactId>
  <version>11</version>
</dependency>

<dependency>
  <groupId>android.support</groupId>
  <artifactId>compatibility-v13</artifactId>
  <version>11</version>
</dependency>
```

If you find that the above `<dependency>` fails due to conflicts, your project and it's dependencies may both depend on the compatibility extra.  The first option is to add an `<exclude>` clause to each dependency that uses the library, as [described here](https://groups.google.com/forum/#!msg/actionbarsherlock/2cLR48IArck/U8--60QxeTkJ).  This works with command line builds but it may not work with your IDE.

If you have problems with `<exclude>`, another option is to override the `<groupid>`, `<artifactid>`, and `<version>` properties used by the deployer to match Google's published library.

Use one of the following `<dependency>` instead of those shown above.
Note that `<version>` begins with a letter, e.g. `r11`.

```xml
    <dependency>
      <groupId>com.google.android</groupId>
      <artifactId>support-v4</artifactId>
      <version>r11</version>
    </dependency>

    <dependency>
      <groupId>com.google.android</groupId>
      <artifactId>support-v13</artifactId>
      <version>r11</version>
    </dependency>
```

Then override `support-v4` or `support-v13` during installation:

    mvn install -Dextras.compatibility.v4.groupid=com.google.android \
                -Dextras.compatibility.v4.artifactid=support-v4 \
                -Dextras.compatibility.v4.version.prefix=r

    mvn install -Dextras.compatibility.v13.groupid=com.google.android \
                -Dextras.compatibility.v13.artifactid=support-v13 \
                -Dextras.compatibility.v13.version.prefix=r

In order to use v7 extra, both dependencies (apklib & jar) are needed

```xml
<dependency>
  <groupId>android.support</groupId>
  <artifactId>compatibility-v7-gridlayout</artifactId>
  <version>11</version>
  <type>apklib</type>
</dependency>

<dependency>
  <groupId>android.support</groupId>
  <artifactId>compatibility-v7-gridlayout</artifactId>
  <version>11</version>
  <type>jar</type>
</dependency>
```

For the Google Analytics extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.analytics</groupId>
  <artifactId>analytics</artifactId>
  <version>2</version>
</dependency>
```

For the Google AdMob Ads extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.admob</groupId>
  <artifactId>admob</artifactId>
  <version>6.4.1-r11</version>
</dependency>
```

For the Google Cloud Messaging Library extra client library (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.gcm</groupId>
  <artifactId>gcm-client</artifactId>
  <version>3</version>
</dependency>
```

For the Google Cloud Messaging Library extra server library (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.gcm</groupId>
  <artifactId>gcm-server</artifactId>
  <version>3</version>
</dependency>
```
    
For the Android annotations tools 

```xml
<dependency>
  <groupId>com.google.android.annotations</groupId>
  <artifactId>annotations</artifactId>
  <version>20.0.3</version>
  <scope>provided</scope>
</dependency>
```

For the uiautomator jar

```xml
<dependency>
  <groupId>android.test.uiautomator</groupId>
  <artifactId>uiautomator</artifactId>
  <version>4.1.2_r4</version>
  <scope>provided</scope>
</dependency>

<dependency>
  <groupId>android.test.uiautomator</groupId>
  <artifactId>uiautomator</artifactId>
  <version>4.2.2_r2</version>
  <scope>provided</scope>
</dependency>
```
    
For the Google Play Services extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.gms</groupId>
  <artifactId>google-play-services</artifactId>
  <version>5</version>
  <type>apklib</type>
</dependency>
<dependency>
  <groupId>com.google.android.gms</groupId>
  <artifactId>google-play-services</artifactId>
  <version>5</version>
  <type>jar</type>
</dependency>
```

For the Google Play APK Expansion extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.apk.expansion</groupId>
  <artifactId>play-apk-expansion-downloader</artifactId>
  <version>2</version>
  <type>apklib</type>
</dependency>
<dependency>
  <groupId>com.google.android.apk.expansion</groupId>
  <artifactId>play-apk-expansion-zip</artifactId>
  <version>2</version>
  <type>apklib</type>
</dependency>
```

For the Google Play Licensing extra (ATTENTION! Do NOT use provided scope!!)

```xml
<dependency>
  <groupId>com.google.android.licensing</groupId>
  <artifactId>play-licensing</artifactId>
  <version>2</version>
  <type>apklib</type>
</dependency>
```

To install only a specific module use

    mvn clean install -N

in any parent folder of the desired package and then the usual
                                  1
    mvn clean install

For example to install only the compatibility v4 extra you can do the
following

    mvn clean install -N
    cd extras
    mvn clean install -N
    cd compatibility-v4
    mvn clean install

Similar for only API level 12 add on use

    mvn clean install -N
    cd add-ons
    mvn clean install -N
    cd google-apis-12
    mvn clean install

The same could be done with deploy


How To Use for Deploying Onto Remote Server
-------------------------------------------

The above deployment works fine for one machine, but what if you need
to supply a whole team of developers and a cluster of build machines
with the artifacts.

As a condition you need to have a repository server used by all
those machines and the following process will deploy to this server,
which will in turn provide the artifacts to all the machines.

Edit the repo.url property in the pom.xml to point to the repository
you want to publish to and then add a server with the credentials to
your settings.xml.

```xml
<settings>
  <servers>
    <server>
      <id>android.repo</id>
      <username>your username</username>
      <password>your password</password>
    </server>
  </servers>
</settings>
```

Run the command

    mvn deploy

in the root folder of this project (same as README you are just
reading), you can also use the same profile options for the different
api level. As a result you should find the artifact in the repository
of your remote server

For more information about this stuff look at the documentation for
the maven-deploy-plugin.


Javadoc
-------

It is possible to create javadoc artifacts for the platforms
where available in the sdk. To call it use

    mvn clean install -Pall,with-javadoc

and the respective javadoc jars will be created and also installed.
This also works for deployment to a repository server

    mvn clean deploy -Pall,with-javadoc

Mailinglist - Questions
-----------------------

Please direct any questions to the community at the Maven Android
Developers mailing list at
http://groups.google.com/group/maven-android-developers
 
Known problems
-------------

- Platforms and Add on folder names changes in SDK

When updating an existing android sdk install the add-ons subfolder
can sometimes be reused and their contents be updates so you could end
up with e.g. the google maps-4r2 in a folder named
google_apis-4_r01. To work around this just uninstall the affected
add-on and reinstall it with the android sdk tool.

Similarly the platform specific folder used to be e.g. android-1.5 and
is now android-3 using the api level as the numeric identifier. If
your SDK install uses the old folder names for any platform simply
reinstall that platform with the android tool.

In a similar manner the folder for the support libraries in the the sdk
used to be compatibility and is now support

The Add ons used different folder names as well. The Maven Android SDK
Deployer' is adapted to the lastet naming
scheme. To do that yourself remove all "Google APIs by Google Inc" in
the android SDK manager and install them again.

Issues
------

If you find any problems or would like to suggest a feature, please
feel free to file an issue on github at
http://github.com/mosabua/maven-android-sdk-deployer/issues

Potential todo items
--------------------

- add custom pom files for install/deploy that eg. define dependency
  from maps to android jar

- maybe some sort of reporting of errors, failures and success as well
