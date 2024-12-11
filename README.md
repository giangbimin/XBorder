# XBorder
Bridging the Gap Between Digital Ecosystems: My Vision for a Unified Software Platform

## Overview
In today’s world, mobile devices are steadily closing the gap with traditional computers in terms of functionality. With their powerful processors, high-resolution displays, storage options, and multimedia capabilities, they’re almost as capable as desktops or laptops. However, differences in operating systems and software often prevent us from fully utilizing the potential of these devices together.

## The Problem: Fragmentation and Wasted Resources

Imagine having a desktop computer—powerful but lacking peripherals like a display, keyboard, speakers, or camera. Then imagine owning a tablet with a stunning 4K screen, excellent speakers, versatile apps, and ample storage. Wouldn’t it be wasteful to buy additional peripherals for the desktop when you already have these features in the tablet?

This very scenario inspired me to explore a way to combine these devices seamlessly.

## My Story

I own a Mac Mini running macOS and a Xiaomi Pad 5 tablet with a gorgeous display. Life was going smoothly until one day, my 4K monitor started showing a dead third of the screen. To make matters worse, my employer faced financial challenges, ending the project I was working on and leaving me without the work devices I relied on.

Facing these setbacks, I felt it was impractical to spend money on a new monitor, webcam, microphone, and other accessories for my personal Mac Mini when I already had a capable tablet. This prompted my journey to repurpose my tablet as a powerful peripheral for my Mac Mini.

## The Vision
I envisioned turning my tablet into an all-in-one peripheral for my Mac Mini, capable of:

- Acting as an external display with adjustable brightness and high refresh rates.
- Serving as a speaker to play audio from the Mac Mini.
- Functioning as a webcam or microphone using the tablet’s front/rear cameras, with options for filters and effects.
- Providing additional storage by utilizing the tablet’s SSD as a dedicated drive for the Mac Mini.
- Enabling touch input or gesture recognition for macOS, possibly leveraging AI for advanced interactions.
- Acting as a hub for peripherals like headphones, Bluetooth keyboards, and mice without directly connecting them to the Mac Mini.
- Sharing its mobile internet connection with the Mac Mini.
- For Phase 1, I focused on using USB 3 or Ethernet for communication, ensuring sufficient bandwidth for tasks like streaming 4K video at 60 fps. Among these features, the ability to use the tablet as an external display and speaker was my top priority.

## The Journey
I began exploring ways to use my tablet as an external display:

### Initial Attempts:

I tried using an adapter to capture the Mac Mini’s screen output and stream it to the tablet using apps like Orion. While feasible in theory, the setup resulted in significant lag, making it unsuitable for practical use.
Next, I explored macOS’s Sidecar feature, which is designed for iPads. Unfortunately, it required an existing monitor to set up and didn’t work well outside the Apple ecosystem.
Through these trials, I realized the pros and cons of existing solutions:
- *Advantages*: Easy to set up with minimal installation.
- *Limitations*: Most apps required payment, delivered subpar screen quality (limited to HD or low refresh rates), and couldn’t transfer audio or utilize the tablet’s camera effectively. Furthermore, I found no robust macOS-to-Android solutions.

### The Breakthrough:
Determined to find a better solution, I started researching programming techniques and frameworks to build my own app. My reading list included:
- Apple’s DriverKit documentation
- Open-source projects like ScreenCaptureKit
- Tutorials on monitor control and screen brightness adjustment.
- My findings led to two potential approaches:

1. **Method 1** Use ScreenCaptureKit to stream screen, audio, and other data via TCP from the Mac Mini to the tablet. However, this method had performance limitations and didn’t allow for screen brightness adjustments.
1. **Method 2** Create virtual devices for all resources (display, audio, storage, etc.). This method provided better customization and performance but required an in-depth understanding of macOS and Android system cores.

### Continue 

......




## Research Sources

### 1. ScreenCaptureKit with TCP Streaming  
This approach focuses on streaming media (screen, audio, etc.) between devices using ScreenCaptureKit and TCP. Additionally, I explored creating virtual devices for greater control over resolution and brightness.  

- [Over 500 Nits Failed](https://alinpanaitiu.com/blog/over-500nits-failed/)  
- [Journey to DDC on M1 Macs](https://alinpanaitiu.com/blog/journey-to-ddc-on-m1-macs/)  
- [MonitorPanel - GitHub](https://github.com/alin23/monitorpanel/blob/nits-limit/Sources/monitorpanel/main.swift)  
- [CGVirtualDisplay on GitHub](https://github.com/KhaosT/CGVirtualDisplay/blob/main/VirtualDisplayExp/CGVirtualDisplayPrivate.h)  
- [MonitorControl - GitHub](https://github.com/MonitorControl/MonitorControl)  

---

### 2. Remote Framebuffer Protocol (RFB)  
The RFB protocol (RFC 6143) enables efficient streaming of data and interactions between devices. This includes caching data and supporting bidirectional syncing.  

- **Advantages**: Optimized for caching and interactive data flow.  
- **Challenges**: Building a protocol stack is complex.  

Relevant Resources:  
- [RFC 6143 Documentation](https://github.com/rfbproto/rfbproto)  

---

### 3. Scrcpy  
Scrcpy is an open-source tool that allows control of an Android device using a computer's keyboard and mouse. It supports various features without requiring root access:  

- Audio forwarding via USB or TCP/IP.  
- Screen mirroring with configurable quality.  
- Camera mirroring (Android 12+).  
- Recording and clipboard sharing.  
- Physical keyboard, mouse, and gamepad simulation.  
- Linux-only webcam mirroring (V4L2).  

GitHub Repository:  
- [Scrcpy](https://github.com/Genymobile/scrcpy)  

---

### 4. Syphon Framework  
Syphon is an open-source macOS framework for real-time video and image sharing between applications. It integrates with tools like Quartz Composer, Max/Jitter, and FFGL.  

GitHub Repository:  
- [Syphon Framework](https://github.com/Syphon/Syphon-Framework)  

---

### 5. Data Transfer Utilities  
For transferring data and enabling USB communication between devices, the following tools were explored:  

- [USB Serial for Android](https://github.com/mik3y/usb-serial-for-android)  
- [Android External USBIP](https://github.com/trevd/android_external_usbip)  
- [OpenMTP - Advanced Android File Transfer Application for macOS](https://github.com/ganeshrvel/openmtp)
