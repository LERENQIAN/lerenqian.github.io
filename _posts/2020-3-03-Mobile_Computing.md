---
layout: post
category: Computer Science
published: true
tags:
  - CS
title: Mobile Computing Summary
---

**2020.03.03_Review_for_CSE535:**
Mobile-Computing-System-Models/Context-Aware-Computing/Mobile-Security/Mobility/Power-and-Energy/IOT;

**Programming**: Java(Android Studio) ;

**Optional**: CUDA_C, Posenet(tensorflow required);

Mobile Computing
----------------

### Chapter 1

#### Mobile Computing System Models

1.  Smartphone: Constraints:location tracking and the type of applications that
    can run on a smartphone

2.  Smartphone + Cloud: The interception of private data, the load on the cloud
    affecting server availability and reliability, and the tradeoff between
    computation and communication times

3.  Fog Server: located closer to a user, there is a decrease in communication
    time. Fog servers are also able to support multiple communication protocols,
    such as Bluetooth and WiFi.

4.  External Sensors

5.  Cloudlets: devices around you, may not in the same network (e.g. other
    people's smart phones)

Example: fog/cloud server communication/computation ability tradeoff

### Chapter 2

#### Context-Aware Computing

1.  Adaptation（system & user） --\> context awareness Context: relevant data to
    derive outputs Use machine learning to classify(prediction) Functionality:
    Presentation of information/Execution/Tagging info to support later
    retrieval/Adaption of behavior and appearance

    ![1](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/1.jpg)

Example: Prediction using finite state Markov chain

### Chapter 3

#### Mobile Programming

1.  Android Studio

2.  Android Multithreading Process(RAM):

    -   code memory (shared memory)

    -   global parameter (shared memory)

    -   stack (private thread)

    -   heap (shared memory) Content Provider: because threads in different
        processes cannot communicate Massage Passing Interface (MPI): socket
        engineering

    -   activity/background thread

    -   handler: different handler class to control the interaction of threads

        ![2](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/2.jpg)

-   bound/unbounded service

    ![3](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/3.jpg)

1.  Graphics Processing Unit (GPU) Programming (CUDA_C)

    ![4](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/4.jpg)

### Chapter 4

#### Mobile Security

1.  Cryptography

    -   text encryption (KS symmetric)

    -   communication encryption (sender/receiver; public/private key system
        (RSA))

    -   massage integrity (Authentication methods)

        ![5](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/5.jpg)

2.  Attack types:

    -   Perturbation attack(presentation attack): attack by utilizing inputs

    -   Causative attack: attack by changing params of model

    -   Black box attack/ white box/ grey box

        ![6](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/6.jpg)

        ![7](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/7.jpg)

        ![8](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/8.jpg)

### Chapter 5

#### Tackling Mobility for Communication

1.  Location Management

    -   Operations: search/registration/update/handoff

    -   Tradeoff: handoff/search

    -   Location Registers (Home LR)

    -   Time-to-live(TTL): to restrain the search cost

    -   Forwarding Pointers (flat replication/hierarchical replication :
        tradeoff between update & search)

        ![9](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/9.jpg)

2.  Mobile IP

    -   Domain Name Service (DNS): change name for IP

    -   IPv4

    -   IPv6

        ![10](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/10.jpg)

        ![11](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/11.jpg)

Example: Location Management using TTL;

### Chapter 6

#### Power and Energy

-   power/energy; utilization/duty cycle; timer resolution

-   challenges(CPU power benchmarking (a model-based power measurement) can have
    large variances in a set of data points, which can cause a large margin of
    error. Context-aware applications, such as an auto-screen brightness
    controller, use a different amount of power based on the environment.
    Without the ability to fully isolate applications, background threads can
    affect the power consumption measurements of an application.)

    ![12](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/12.jpg)

Example: power consumption evaluation for different modes (lazy/eager, WIFI/4G)

### Chapter 7

#### Internet of Things (IoT)

-   Cyber Physical Systems (CPS)

    ![13](https://raw.githubusercontent.com/lerenqian/lerenqian.github.io/master/_posts/image/Mobile_Computing/13.jpg)

### Assignment and Project

#### Assignment:

1.  design a UI interface using Android Studio

2.  get sensor informations(accelerometer info in Android phone) and plot in the
    UI

3.  make database (sql.db) in phone sd memory

4.  upload sensor info (db file) to flask local server

5.  download db file from local server using flask to sd card

6.  plot data info into the UI with the downloaded info

#### Project - part 1:

1.  display the video (American signal language)

2.  record videos using camera (record practicing videos)

3.  upload recorded videos in local server using flask

#### Project - part 2:

1.  cut recorded videos into slices(png) using posenet

2.  extract data from png into json using posenet

3.  (optional) transform json into csv using posenet

4.  train data

5.  package trained models into pkl files

6.  upload pkl files and flask app.py file into cloud server(by coursera)

7.  cloud server execute app.py and send test data to pkl models to predict

8.  return labels after prediction
