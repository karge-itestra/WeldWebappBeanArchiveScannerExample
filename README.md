# WeldWebappBeanArchiveScannerExample
An example for the bug discussed in https://issues.redhat.com/browse/WELD-2570

To set up the example, import the Maven project into IntelliJ, and set up a run configuration with the SmartTomcat plugin like shown in the image.

![SmartTomcat Setup](/IntelliJ_SmartTomcat_Run_Configuration.png)

Note that there is a potential issue with the setup of the project, since the `beans.xml` file does not reside in the `webapp` folder which is used as web root, but in the `resources` folder. Only the `META-INF` folder in the `resources` directory is found by both the `DefaultBeanArchiveScanner` and the `WebappBeanArchiveScanner`. Nonetheless, even if the `META-INF` folder in the `resources` directory is not best practice, since it is easy to make Weld resilient against it, I would advise for it.

Fix: See https://github.com/weld/core/pull/2003 and https://github.com/weld/core/pull/2004
