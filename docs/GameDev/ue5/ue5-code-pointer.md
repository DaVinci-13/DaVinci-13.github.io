---
title:    Pointer Types
layout:    doc
date:   2023-08-09 17:36:00 +0800
categories:    ue5, code, pointer
---

# Pointer 指针

## The * and &(取址符) Symbols in Context

|Symbol|Code Examples|Context|Syntax|Meaning|
|---|---|---|---|---|
|*|UActor *ActorPtr;|Declaring| UActor * |Point to UActor|
||CopyofActor=*ActorPtr;|Using| *ActorPtr |Contents at ActorPtr|
|&|UActor &ActorRef;|Declaring| UActor & |Reference to UActor|
||ActorAddress=&Actor;|Using| &Actor <br> &ActorRef |Address of Actor or ActorRef|

## ->