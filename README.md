# Overview Setup 

* Java install
* Scala
* SBT
* Spark

The Google Cloud Shell provides a consistant free compute environment

    \
    +---------------------+
    | Computer OS - Linux |
    |                     |
    |                     |
    |                     |
    |                     |
    |                     |
    |                     |
    +---------------------+

# Setup Components
## Checking Java Installation

In this step, we will confirm we have Java installed on the machine

    \
    +------------------------+
    | Computer OS - Linux    |
    | +---------------------+|
    | | Java Virtual Machine||
    | | (JVM)               ||
    | |                     ||
    | |                     ||
    | +---------------------+|
    +------------------------+

See what version of java you have
    java -version

Check that you can compile jars
    javac -version

**TODO** WHAT IF NO JAVA?!

## Installing Scala

In this step, we will confirm we have Scala installed on the machine

    \
    +---------------------------------+
    | Computer OS - Linux             |
    |+----------------------++-------+|
    || Java Virtual Machine || scala ||
    || +------------------+ ||       ||
    || | Scala (JAR)      | |+-------+|
    || |                  | |+-------+|
    || |                  | || scalac||
    || +------------------+ ||       ||
    |+----------------------++-------+|
    +---------------------------------+

Try:

    scala -version

Not found?

Time to install:

    sudo apt install scala -y

Check scala version:

    scala -version

You should have a version number

## Installing sbt
The Simple Build Tool (sbt) is a packaging tool that helps manage dependencies in Scala.
It is akin to Maven (mvn) or Rake

    \
    +---------------------------------+
    | Computer OS - Linux             |
    |+----------------------++-------+|
    || Java Virtual Machine || sbt   ||
    || +------------------+ ||       ||
    || | Scala (JAR)      | |+-------+|
    || |                  | |+-------+|
    || |                  | || scalac||
    || +------------------+ ||       ||
    |+----------------------++-------+|
    +---------------------------------+

Try:

    cd ~

    curl -L https://piccolo.link/sbt-1.3.0.tgz | tar xvz -C .

## Installing Spark

In this step, we will confirm we have Apache Spark installed on the machine.

    \
    +---------------------------------+
    | Computer OS - Linux             |
    |+-----------------++------------+|
    || Java (JVM)      ||spark-submit||
    ||+---------------+||            ||
    ||| Scala (JAR)   |||            ||
    |||+-------------+||+------------+|
    |||| Spark (JAR) |||              |
    ||||             |||+------------+|
    ||||             ||||spark-shell ||
    |||+-------------+|||            ||
    ||+---------------+||            ||
    |+-----------------++------------+|
    +---------------------------------+

This also includes some shell utilities to provide other ways of executing Spark code.
* spark-submit: Executes pre-packaged code in a JAR file
* spark-shell: Interactive console (REPL) for running spark commands

Try (link below might change):

    cd ~
    curl http://mirror.intergrid.com.au/apache/spark/spark-2.4.4/spark-2.4.4-bin-hadoop2.7.tgz | tar xvz -C .

Check that it's there:

    ls 
    cd spark-2.4.4-bin-hadoop2.7/bin
    ls

Run a spark shell

    ./spark-shell

Wait for it.....

Yay a shell!

    println("Hello World")

# Preparing Project
    cd ~/data-transformations
    ~/sbt/bin/sbt

# Basic Repo for working with Spark + Scala
The purpose of this repo is to make sure you have everything set up to build and run a spark project locally.

## Pre-requisites
Please make sure you have the following installed
* Java 8
* Scala 2.11
* Sbt 1.1.x
* Apache Spark 2.4 with ability to run spark-submit locally

## Setup for local building and testing
* Clone this repo
* Build: sbt assembly
* Test: sbt test

Please confirm that all of the tests pass.

## Setup for local run with spark-submit
After running

    sbt assembly
from the root directory run

    spark-submit target/scala-2.12/data-transformations-assembly-0.1.jar 

to run the spark job locally.

Confirm that you see "Hello Spark" in the output.

If all the test passed locally and "Hello Spark" was in the output than your environment is set up and ready for a TW Data Engineering coding interview.

