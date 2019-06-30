# Vicon-dataStream

Adapted from Vicon Datastream SDK (https://www.vicon.com/products/software/datastream-sdk) for streaming motion capture data using TCP/IP protocal from Nexus, Blade, Shōgun, and Tracker applications to another computer and on different softwares. Please note that in Vicon's SDK download, they forgot to include the <code>IDataStreamClientBase.h</code> header file.

Please find the Linux and Windows version on Vicon website.

#### 1. Download the folder

<code> gitclone https://github.com/tianshu-z/Vicon-dataStream </code>


#### 2. Change the current directory to where your folder is located. For example:

<code> cd Documents/Vicon-dataStream/Mac/ </code>


#### 3. Run the script with full data stream

<code>./vicon-test 172.28.146.79:801</code>

Please note that you should modify <code>ViconDataStreamSDK_CPPTest.cpp</code> file based upon your needs. The process is as follow:

I. Use your text editor to comment out some unnecessary output of the <code>ViconDataStreamSDK_CPPTest.cpp</code> script. Save and rename it, for example 
<code>ViconDataStreamSDK_CPPTest_dataStream.cpp</code> 

II. Run the following command line in your terminal. This will compile to a binary <code>vicon-dataStream</code>.

<code>g++ ViconDataStreamSDK_CPPTest_dataStream.cpp -L $PWD -lViconDataStreamSDK_CPP -o vicon-dataStream</code>

III. Specify the IP address and you should be able to connect to your MoCap hosting computer.

<code>./vicon-dataStream 172.28.146.79:801</code>


I have another example, <code>perf-ieeegem</code>, compiled from <code>ViconDataStreamSDK_CPPTest_dataStream_sliced.cpp</code>. I used it for real-time music composing based on the captured dancer movements in a performance during the IEEE Games Entertainment & Media Conference 2019. Becuase Max/MSP cannot digest too much information all at once, I have to only keep the translation value information of the markers that I need before it is streamed into the software. Here in this case, the C++ file.

In Max/MSP, I used <code>shell</code> object (https://github.com/jeremybernstein/shell/releases/tag/1.0b2) and <code>zl</code>object (https://docs.cycling74.com/max5/refpages/max-ref/zl.html). If you only want to bring the object tracking data from Vicon Tracker out to another software like Max/MSP, you should try <code>udpstream</code> before going this route.


We also used the same method to stream data into an autoencoder neural network (https://github.com/mariel-pettee/choreography) and then a localhost webpage in real time.


### Supplimentary:

I have a sample included in this repository. In this sample, you can use hands (specifically the joints of phalanges and metacarpal bones on your index fingers) to control the volume of the sound and the height of your body (specifically T10, the center on your back).


Prerequisite: 

<a href = "https://cycling74.com/">Max 8</a> (Max 7 should work but I didn't test it on 7.)

<a href = "https://github.com/jeremybernstein/shell/releases/tag/1.0b2">Shell library </a> for Max/MSP

<a href = "https://www.vicon.com/">Vicon Motion Capture System</a>

Vicon Shogun Software and full body tracking set up. (Note: unlike udp streaming on Vicon Tracker, you don't need to do any pre-setup for out data streaming here. It just runs.)

macOS


1. Open your terminal

2. Download the repository

<code> gitclone https://github.com/tianshu-z/Vicon-dataStream </code>


3. Change your directory

<code> cd Vicon-dataStream/Mac/ </code>

4. Open up the Max/MSP patcher <code>dataStream-test_sineWave.maxpat</code> in the folder. You need to change the directory to your. Right now, it is <code>/Users/zoe/Vicon-dataStream/Mac/dataStream.log</code>

5. In the terminal, run

<code>./vicon-test 172.28.146.79:801 | dataStream.log</code>

6. Run your max patcher

You should be able to see data stream on both your terminal and your max console, which also means you can hear the sinewave now.
