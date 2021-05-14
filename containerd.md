Containerd is supported by both Linux and Windows. Containerd is daemon, which acts as an interface between your container engine and container runtimes.

It provides an abstracted layer that makes it easier to manage container lifecycles – such as image transfers, container executions, snapshot functionality, and certain storage operations through the use of simple API requests.

This avoids the hassle of making multiple, low-level system calls. As those system calls can vary from platform to platform, this also makes containers more portable while allowing the API to remain fundamentally the same.

Like runC, containerd is another core building block of the Docker system, which has been spun off as an independent, open-source project.

![](https://github.com/amarnadh19/books/blob/main/images/containerd_1.jpg)

