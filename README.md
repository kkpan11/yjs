
# ![Yatta!](./extras/imgs/Yatta_logo.png?raw=true)

A real-time web framework that manages concurrency control for arbitrary data structures and is _not_ based on Operational Transformation.
Yatta! provides similar functionality as [ShareJs](https://github.com/share/ShareJS) and [OpenCoweb](https://github.com/opencoweb/coweb)
but does not require you to understand how the internals work. The predefined data structures provide a simple API to access your shared data types.

Predefined data structures:
* Text
* Json - [example](./examples/IwcJson.md)
* XML (coming soon)

Unlike other frameworks, Yatta! supports P2P message propagation and is not bound to a specific communication protocol.

Currently supported communication protocols:
* [IWC](dbis.rwth-aachen.de/gadgets/iwc/resources/iwc.manual.pdf) - Inter-widget Communication

# About
Find out more about the concurrent editing problem here
([Cooperation, Concurrency, Conflicts, and Convergence](http://opencoweb.org/ocwdocs/intro/openg.html)) and here
([Operational Transformation (OT)](http://en.wikipedia.org/wiki/Operational_transformation))

My Bachelor Thesis project aim was to develop a P2P OT Framework that enables collaboration on XML documents and supports
[Intention Preservation](http://www3.ntu.edu.sg/home/czsun/projects/otfaq/#intentionPreservation).
After some time I realized that OT has significant drawbacks in P2P environments.

With my gained experiences I came up with a new approach. I named it Yata - Yet Another Transformation Approach.
Very surprising is that my approach enables concurrent editing with the following space and time properties:
* Time complexity: O(S), whereby S is the number of operations that are inserted concurrently at the same position. This means that my approach does not transform against operations that happen on other positions.
* Space complexity = O(|Document|), whereby |Document| is the size of shared document. Depending on the used data structure, Yata may needs 4*|Document| of space.
This means that my approach beats all OT time complexities. Furthermore, it is possible to make a very strict definition of Intention Preservation, and I was able to
show that it is never violated.

Another advantage of my approach is that propagated messages are very small.
Background: In Real-Time P2P OT algorithms you have to send a state-vector with every message that defines the state of the History Buffer
on which the operation was created. This is not necessary in Yata.

One downside is that the History Buffer holds at least as many operations as there are characters in the document.
In contrast, an OT algorithm can have an empty History Buffer while the document size is very big.

So, how did I come up with the name for the implementation (Yatta! is not Yata)?
![YATTA!](./extras/imgs/YATTA.png)
Yatta! means "I did it!" in Japanese. You scream it when you accomplish something you are proud of (for proper application I refer to the Yatta-man in [Heroes](http://heroeswiki.com/Yatta!)).
There is also this awesome video on the Internet that will change your life [Yatta](https://www.youtube.com/watch?v=kL5DDSglM_s).
# Status
Yatta!is still in an early development phase.

# Support
Please report any issues to the Github Issue

# License
Yatta! is licensed under the [MIT License](./LICENSE.txt).