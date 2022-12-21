# What's a container

Most [[operating system]]s has something called a [[kernel]] that works like an [[API]] between [[physical hardware]] and [[system process]]es. For example, if you have made an [[Node.js]] app that writes a file to the [[hard drive]], it actually is telling the [[kernel]] to create this file not the [[hard drive]] itself.

These interactions with the [[kernel]] are made by using something called [[system call]]s.

We can use [[namespacing]] for [[isolating resources per process]] (or group of processes), [[control groups]] to limit amount if resources used per process.

A container is basically that - it is a process, that issues calls to [[kernel]] and has isolated resources like [[hard drive]], [[network access]], [[ram]], [[cpu]]. It is built using an [[image]] which basically consists of a [[file system snapshot]] and [[startup command]]s.