
# TCPmyUDP
(preᵖʳᵉ alpha release) An insanely fast (and simple) udp2raw alternative implemented in Rust (btw).

Make your UDP traffic look like generic TCP traffic, bypass UDP blocks and Firewalls in seconds.

## About
Story why I've decided to create this Project:

I'm on my way to become a Network Engineer and as we know, learning by doing is one of the fastest ways to learn. I'm certain I will gain a lot of knowledge about network packages and the way they work in a network, by creating this program.

I'm using a crappy old Laptop for school and most of the time it's are so slow it becomes a challenge to even open my notes. Why to bother with the Laptops performance when I have a plenty powerful Arch Linux machine sitting at home. So I set up [Sunshine](https://github.com/LizardByte/Sunshine) and [Moonlight](https://github.com/moonlight-stream), connected to my Homenetwork using WireGuard and... Nothing. I couldn't connect to my PC for some reason. A quick `ping 8.8.8.8` confirmed the lack of network connectivity. Connecting to my Proxmox host using Tailscale and checking my WireGuards server logs confirmed a handshake to my client hasn't been made. Using OpenVPN over TCP as fallback worked. This made me believe my Schools WiFi was blocking UDP (or at least the WireGuard Protocol due to Deep Packet Inspection). Trying WireGuard (and OpenVPN) over UDP on port 53, which is used for DNS, revealed even that is blocked.

While TCP was an option, it was a rather bad one. There are many reasons why TCP is terrible for Live Streaming. You don't need TCPs reliability, error checking, flow control, out-of-order packet sorting, and whatnot for a steam. You're pushing at least 60 Frames a seconds through the Tunnel, you don't care if a single frame gets lost as long as the connection is not interrupted because TCP is waiting for a new package. This issue doesn't exist with UDP due to its connectionless nature. Frankly speaking, UDP doesn't give a fuck.

Shortly after, I discovered [udp2raw](https://github.com/wangyu-/udp2raw), which seemed like the thing I just needed. Unfortunately it is incredibly inconvenient and unnecessarily complex to set up. I got it to work and let me tell you it **works**. It works really well.

I would definitely continue to use it if it wasn't so *hard* to use.

Anyway, this is what inspired me to make this project. ***TCPmyUDP***, A simple to use (and faster) [udp2raw](https://github.com/wangyu-/udp2raw) alternative.

## The Problem
I. suck. at. Rust.

Yes, I come out of nowhere and decide to build something that is probably not recommended for beginners.

This will mark the beginning of my serious Rust journey. I will probably write a Blog where I tell you guys more about the inner working of TCPmyUDP (and my journey).
