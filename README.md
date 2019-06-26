# Vicon-dataStream

Adapted from Vicon Datastream SDK (https://www.vicon.com/products/software/datastream-sdk) for streaming motion capture data using TCP/IP protocal from Nexus, Blade, Shōgun, and Tracker applications to another computer and on different softwares. Please note that in Vicon's SDK download, they forgot to include the <code>IDataStreamClientBase.h</code> header file.

Please find the Linux and Windows version on Vicon website.

#### 1. Download the folder


#### 2. Change the current directory to where your folder is located. For example:

<code> cd Documents/Vicon-dataStream/Mac/ </code>


#### 3. Run the script with full data stream

<code>./vicon-test 172.28.146.79:801</code>

Please note that you should modify <code>ViconDataStreamSDK_CPPTest.cpp</code> file based upon your needs. The process is as follow:

I. Use your text editor to comment out some unnecessary output of the <code>ViconDataStreamSDK_CPPTest.cpp</code> script. Save and rename it, for example 

<code>ViconDataStreamSDK_CPPTest_dataStream.cpp</code> 

II. Run the following command line in your terminal. This compile to a binary <code>vicon-dataStream</code>.

<code>g++ ViconDataStreamSDK_CPPTest_dataStream.cpp -L $PWD -lViconDataStreamSDK_CPP -o vicon-dataStream</code>

III. Specify the IP address and you should be able to connect to your MoCap hosting computer.

<code>./vicon-dataStream</code>

I have another example, <code>perf-ieeegem</code> compiled from <code>ViconDataStreamSDK_CPPTest_dataStream_sliced.cpp</code>. I used it for real-time music composing based on dancer movement in a performance in IEEE Games Entertainment & Media Conference 2019. Becuase Max/MSP cannot digest too much information all at once, I have to only keep the translation value information of the markers that I need before it is streamed into the software.

In Max/MSP, I used <code>shell</code> object (https://github.com/jeremybernstein/shell/releases/tag/1.0b2) and <code>zl</code>object (https://docs.cycling74.com/max5/refpages/max-ref/zl.html). If you only want to bring the object tracking data from Vicon Tracker out to another software like Max/MSP, you should try <code>udpstream</code> before going this route.


We also used the same method to stream data into a autoencoder neural network (https://github.com/mariel-pettee/choreography) and then a localhost webpage in real time.
