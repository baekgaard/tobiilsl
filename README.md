tobiilsl
========

This is a simple [Lab Stream Layer][1] interface to acquire data from a Tobii Eye Tracker, using the [Tobii Pro SDK][2]. 

It does NOT work with the previous [Tobii Pro Analytics SDK 3][3], which is a somewhat different API and -- in particular --
has very different timing and synchronization models.

It works by connecting to an attached eye tracker (it uses the first one it finds, including any local USB connected 
devices; edit the code if you want something else), installs a licence (if you need that), and creates a stream 
outlet that pushes data from the eye tracker onto the lab streaming layer.

Use
---

To use it, simply install the dependencies (python 2.7 and the libraries pylsl, tobii_research and numpy in particular)
and type from a command prompt:

    python ./tobiilsl.py

This will start the stream outlet. It will print out the (local) timestamp on the console, and every 5 seconds, a log of
the current time and how many packages has been transmitted. Halt it with escape or pressing ctrl-c several times.

Calibration needs to be done prior to starting the acquisition interface using other (Tobii) tools.

A note on time
--------------

The tobiilsl.py interface uses the system timestamp that it receives from the Tobii API, thus compensating for any lag 
and jitter in the tobiilsl.py interface itself. On most installations, the difference between this timestamp and when
the package is injected to the stream outlet is small. Note that the system timestamp created by the Tobii API is 
[synchronized automatically][4] with the device timestamp, so it is a better approximation of the real acquisition timestamp
than when the package is being injected into the stream outlet.

Caveats
-------

It is currently tested with Python 2.7 and runs under Windows 10; it has not been tested on other platforms (partly because
the Tobii 

References
----------

[1]: https://github.com/sccn/labstreaminglayer "Lab Streaming Layer (LSL)"

[2]: http://developer.tobiipro.com/tobiiprosdk.html "Tobii Pro SDK"

[3]: http://developer.tobiipro.com/python/python-oldmigrationsdk.html "Differences from Tobii Pro Analytics SDK"

[4]: http://developer.tobiipro.com/commonconcepts/timestamp-and-timing.html "Tobii time stamps and timing"


License
=======

Created by Per Baekgaard / pgba@dtu.dk / baekgaard@b4net.dk, Juni 2018

Licensed under the MIT License:

Copyright (c) 2018, Per Baekgaard, Technical University of Denmark, DTU Compute, Cognitive Systems Section

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
