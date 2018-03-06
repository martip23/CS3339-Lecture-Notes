# Pin Instructions for CS3339, Spring 2018

## Download

You can download Pin from the Intel website at

https://software.intel.com/en-us/articles/pin-a-dynamic-binary-instrumentation-tool


You can download Pin via the browser on your own PC and then transfer the tar.gz file to your drive
on the CS server using `scp`. Alternatively, you can download it directly on to the CS server with
wget. Note 3.5 is the recommended version. We have not tested the latest version released in February 2018. 

         wget http://software.intel.com/sites/landingpage/pintool/downloads/pin-3.5-97503-gac534ca30-gcc-linux.tar.gz


## Install

To install Pin _locally_ move the downloaded file to where you want to install Pin (home directory is recommended). Unzip and
untar the file  

        tar zxvf pin-3.5-97503-gac534ca30-gcc-linux.tar.gz

This will create a `pin-3.5-97503-gac534ca30-gcc-linux` directory within the current location. For
convenience, you may want to rename this directory to just `pin-3.5`. 

That's it! Pin is now installed. You should be able to see the pin executable with 

        ls -l pin-3.5/

You may want to add the `pin-3.5` directory to your PATH variable so that you don't have to type the
full for the pin executable every time.  
     

## Hello World Example

Pin comes with many pre-defined Pintools. These are located in `pin-3.5/source/tools`. Below are
instructions for running the instcount0 Pintool. You can follow similar steps to run other
pre-defined Pintools. 

        cd source/tools/ManualExamples              # directory with several basic Pintools
        ls                                          # look at a listing of the src (.cpp) files
        make                                        # build all the Pintools in this directory (will take a while)
        ls obj-intel64/                             # object files for 64-bit systems are placed in obj-intel64

        g++ -o fib fibonacci.cpp                    # build a sample program
        ./fib                                       # run program without pin
        pin -t obj-intel64/inscount0.so -- ./fib    # run program inside pin environment (pin executable is in PATH)
        cat instcount.out                           # look at output (number of dynamic instructions)

Note, there are no separate executables for the Pintools. All Pintools are object files (.so)
that are dynamically linked to the pin executable. The instcount


## Further Reading

Pin is a pretty handy tool for performance analysis. If you are interested you can create your own
Pintools to collect a variety of performance characteristics from application binaries. You can look
at the some of the samples example in the `source/tools/ManualExamples` directory. 

Below is a link to API reference. 

https://software.intel.com/sites/landingpage/pintool/docs/81205/Pin/html/group__API__REF.html




