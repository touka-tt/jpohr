# A proposal for a Japanese version of OHR

---

* Written by.
  * Takayuki Tominaga
  * [@touka_tt](https://twitter.com/touka_tt)
* Writing Date
  * 01.05.2020
* Updated Date
  * 14.05.2020

---

## Abstract
* With Corona's recent absence from club events, it's unlikely that events will resume any time soon, even if the urgent call for restraint is lifted in May
* When we tried to build the infrastructure for another distribution event, I found out that there is nothing we can't do, although it will cost some money.
  * It is well known that there are many engineers among hardcore and breakcore artists, and although there are many technical difficulties, the hurdle of implementation may actually be low because all of them are highly IT literate.
* There are online parties abroad like OHR(https://www.facebook.com/ohr.party/), but there are no similar parties in Japan
* It is possible to ask foreign artists to perform at the club because they are not bound by the location, and in a sense, it is possible to achieve something that cannot be done in a normal club.
* M-Project is planning an online party to replace TDOH in the summer, and it seems to be meaningful for the technology verification.
  * If you're going to do it, I think it would be good to have Mr. M-Project join as an observer instead of having him DJ or not.
* It's going to be hard to monetize, but it's simply technically interesting.

## Event Name
### Huub
* It's a wheeled hub with a u(You) added to it.
  * With the meaning of a place that holds you together.
* The source of the association is the Cyber Hub where Kuze connected the refugees in Ghost in the Shell S.A.C. 2nd GIG.
  * I like the way artists in remote values converge in one place through a thin network, reminiscent of wheel rims, spokes and hubs.
  * It would be great if we could create a place to connect artists, DJs, VJs, and audiences who have been scattered due to various influences of the times.
* What do you think?

### Domain
In the meantime, I took the "[huub.club](https://huub.club)".

* I want to make an announcement site in my spare time.
  * A temporary site is now available.
  * The repository is [huubclub/huub-web](https://github.com/huubclub/huub-web).

## Scheduled Date
* Any weekend in May or June.
  * There are many online events in May and we need to prepare for them, so I think it will be June.
  * To be adjusted at 19:00 JST on June 20 (Sat)

## Composition
### Configuration diagram
![HuubDiagram](https://touka1037.github.io/jpohr/HuubDiagramEn.png)
* This is an application of the so-called "Music Unity" method.
  * Linking the DJ's voice to the VJ by relaying the RTMP server
  * Connects to the RTMP server for video relay with video that matches the sound in the VJ
  * Distribution while switching the OBS input on the distribution server
* Overseas performers set up an RTMP server at the performer's place of residence.
  * VirtualNet peering connects foreign and domestic regions' virtual networks
  * Tested on a server in the German region and succeeded in communicating with RTMP
* Twitch will be the destination for the moment.
  * As for music, we have a comprehensive contract with JASRAC, so there is no worry about stopping because of it.
  * No mirroring across multiple sites because of pay-as-you-go billing for traffic leaving Azure's DC.
* I think it's better to do it in one place, because the chat section is also more exciting.
A super-obscure estimate of the cost of Azure's infrastructure is about 300 yen per hour.
  * This does not include servers and their communication costs.
    * We will make another estimate as soon as the speaker is confirmed.
  * That's not including build-out costs, maintenance, etc.
  * I'll just ignore it for now since I've already built it for another event.
* I asked zukutya about it, and he told me that there is a managed service on AWS called MediaLive that specializes in video processing.
  * Consideration is required, including cost.
  * Azure also has a managed service called MediaService (although I've never used it).

### RTMP server for relay
We are using [SRS](https://github.com/ossrs/srs).
I created a DockerImage that runs in low-latency mode and published it.
[https://hub.docker.com/r/touka1037/srs](https://hub.docker.com/r/touka1037/srs)  

```
docker run -p 1935:1935 -p 1985:1985 -p 8080:8080 touka1037/srs:latest
```

## Member
### VJ
* I would like to assign [@touka_tt](https://twitter.com/touka_tt) and [@zukutya](https://twitter.com/zukutya) who is an AWS engineer as VJs.
  * I'm going to have a conversation with him.
  * If it happens, we'll be the VJ duo of Tokyo Gabberdisco!
  * zukutya received. Thank you.

### DJ
* At least for the first time, we want to have people with high IT literacy.
* Since we are not limited by location, we would like to have the cooperation of artists from overseas.
  * So far, our current members are helping us out.
    * DJ Sharpnel
    * Lolistyle Gabbers
    * BrainShit (from Germany)
    * Othermoon

### Monetize
* Monetizing the delivery event is too difficult
* Donation
  * I feel like this is the mainstream of online distribution events.
    * PayPal donation
      * To be honest, I've never used it before, so I'd like to hear if you have any knowledge...
    * Twitch Affiliate Program
      * DJ Sharpnel told me about it. If you apply for it at some place, it seems to pass.
  * The problem with Donation is that we can't make a budget for performance expenses because we can't make a revenue forecast in advance.
    * Equal distribution, initially minus the infrastructure costs?
      * If we take the form of equal distribution, we should disclose the entire cost of infrastructure and so on to the speaker.
      * We need to consult with the performers here. We want to be flexible.

## Intra-group communication
We have created a server in Discord.

# Approximate remaining tasks
1. Several times DJ distribution (I do it personally)
1. Apply for the Twitch Affiliate Program at some place
1. Streamlabs and OBS scene settings
1. Requests for DJs and VJs
1. Set the date
1. rehearsal
1. actual performance
