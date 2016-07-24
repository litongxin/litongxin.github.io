---
layout: post
title: "How to use gatling to do performance test"
description: " Gatling is an open-source load testing framework based on Scala, Akka and Netty"
---

If you want to make your website more attractive, you need elegant design, comfortable font, following user habits, of course a certain number of pictures is essential. When the number of pictures increases, you need to consider the response and performance of your site.

When we need to do performance test, gatling, a lightweight DSL written in Scala, can be a good choice. Simply to say, gatling's principle is:

- divided into specific scenarios
- defined simulation which includes scenario
- run each simulation
- generate a graphical report

#### Simulation Demo:
<img src="/asset/images/simulation-demo.png" width="550px" alt="Simulation Demo"/>

After briefly introducing gatling, in order to develop faster and more convenient, we use the sbt build tool and ready-made plug-ins called io.gatling and gatling-sbt.

#### Implementation with sbt
The directory structure in my local machine as follows :

<img src="/asset/images/directory-structure.png" width="200px" alt="Directory Structure"/>

`build.properties` -  specify sbt version

 <img src="/asset/images/build-properties.png" width="200px" alt="build.properties"/>

`plugins.sbt` - define plug-ins and its versions

 <img src="/asset/images/plugins-sbt.png" width="400px" alt="plugins.sbt"/>

`build.sbt` -  build definition file, which defines the library dependencies

 <img src="/asset/images/build-sbt.png" width="800px" alt="build.sbt"/>

#### Run performance test

-  Run `sbt update` to download dependencies plugins
-  Put your com.myapplication package which contains demoSimulation.scala file to `/scala` directory.
- Run `sbt test` to run gatling test and generate report into
`/target/gatling` directory.

Note: I change the concurrency number from 1 to 50 demoSimulation.scala file, here is the Screenshot for report.
<img src="/asset/images/gatling-report.png" width="800px" alt="build.sbt"/>
