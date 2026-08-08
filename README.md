# ASK-OOK-RF-Remote
Design files for my 433MHz RF remote specifically made to fit into VW Transporter T5/ Golf MK6 2 Button key fob casing.

<img width="504" height="509" alt="image" src="https://github.com/user-attachments/assets/425fc9b4-2674-4d23-b306-9cf5dcd9df62" />

## Introduction

The "key" to this project is to make a functional all-in-one remote key-fob for my VW Polo 6n2. My car came from factory with a key-fob (6N0837219AC) which only had a button for a light to help you find the door or ignition lock. Said key looked like this:

<img width="519" height="397" alt="image" src="https://github.com/user-attachments/assets/bfd34f51-d015-430f-b8ec-0965a43cdf0d" />


Additionally, my car came with a 3rd party alarm system installed from the dealer which I assume used a 433MHz additional remote with a rolling code protocol.

Nonetheless my car only had the spare key (without the light bulb) and the old alarm control unit installed behind the driver's side headlight (non UK car). Since I did not have the knowledge or expertise at the time of buying my Polo 2nd hand (I was 18), instead of getting another remote made from the existing unit, I decided to go the cheap route and buy the Aliexpress special, a 433Mhz ASK/OOK single code receiver with 2 remotes for 7EUR. [Link to the product](https://es.aliexpress.com/item/32966630703.html?spm=a2g0o.order_list.order_list_main.345.2b2e180265tnwY&gatewayAdapt=glo2esp)

At the time it seemed like the right choice since I wanted nothing to do with locking and unlocking my car manually (peasant things). And for a long time it was, however the first problem I noticed is that the quality of the remotes was awful, the switches degraded like crazy and I understood later that using the same single code protocol as the garage doors was not ideal. 

The remote issue I solved by getting another kind of separate remote and to this day it works like a charm after 3 years. Also and on another note, one of the best things about the receiver is that you can pair new remotes on the fly just by pressing the pairing button next to the 13 pin connector.

[Link to the other kind of remote
](https://es.aliexpress.com/item/1005008790564347.html?spm=a2g0o.productlist.main.8.6fdbm5GMm5GM2U&aem_p4p_detail=2026080811291710916937976636560000125169&algo_pvid=d8578ccd-89f3-46d1-b1c1-b2fdf87a9af6&algo_exp_id=d8578ccd-89f3-46d1-b1c1-b2fdf87a9af6-7&pdp_ext_f=%7B%22order%22%3A%2270%22%2C%22eval%22%3A%221%22%2C%22fromPage%22%3A%22search%22%7D&pdp_npi=6%40dis%21EUR%216.59%216.59%21%21%2150.04%2150.04%21%400b8848bf17862137573062011e0e0e%2112000046675551470%21sea%21ES%211662762699%21ACX%211%210%21n_tag%3A-29919%3Bd%3Aed28c003%3Bm03_new_user%3A-29894&curPageLogUid=M3C2liQSV3zS&utparam-url=scene%3Asearch%7Cquery_from%3A%7Cx_object_id%3A1005008790564347%7C_p_origin_prod%3A&search_p4p_id=2026080811291710916937976636560000125169_2)<br>

---

### What problem does it solve?

Here is an image of my current key setup:

<img width="484" height="642" alt="image" src="https://github.com/user-attachments/assets/3cafcbd2-ceb8-4d3e-862a-5b8d9130c2a2" />

As you can see, it doesn't look half bad, however, since I am always carrying many things in my hand and other keys (plus the keychain and remote make noise everytime I hit a road bump). I wanted an all-in-one OEM+ solution. For this I started looking at Golf MK4, MK6 & MK7 remotes and decided to go with the MK6 one. I now is rather bland but its in the middle from being too futuristic(MK7) or too dingy(MK4). 

The good thing is that all remotes share the same HU66 blade and fit on the same kind of cylinder lock, however the transponder is not the same!!! I had to install a new ID44 chip on my new key-fob. 

[Link to the 2 button Golf MK6 key-fob](https://es.aliexpress.com/item/1005005737683184.html?spm=a2g0o.order_list.order_list_main.17.595b1802jJVIsa&gatewayAdapt=glo2esp)

> [!IMPORTANT]
> MK4, MK5, MK6 and MK7 Golf use different transponders, going from the ID48 to the ID88

So I guess months of my life learning PCB design bit by bit would be worth it right? 
Well, for the time being I have to say yes, it was totally worth it and I learned so much in the process and got a Unique OEM+ key for my Polo out of it.

---

### Installation of the Chinese receiver
For those of you that are curious or need a wiring diagram of the OEM installation, here is a small tutorial of how I installed the receiver into my car.

#### OEM alarm 20 Pin Harness diagram


Now here I wont go much into detail, However I have to add this: the Chinese Receiver has to be put into a specific jumper configuration to be able to operate the central pneumatic system that the Polo comes standard with. Moreover, I made the mistake to not write down the wire colors but here they are detailed pin by pin:

<img width="478" height="303" alt="image" src="https://github.com/user-attachments/assets/26f3cb3f-0e6b-4d6c-a283-7038ea0d9d74" />

It's not very detailed, but simply jumping the 12v with what I wanted to actuate worked, so the receiver is most likely just a big box of relays (11v in the case of the LED for some reason unknown to me).

---

Here is a connection diagram of the pins that I used on the receiver and OEM harness:

<img width="858" height="436" alt="image" src="https://github.com/user-attachments/assets/5a777bc8-41f9-4537-92cb-c78f8d446fbb" />


Some of them like the automatic windows did not work correctly (it was spamming like crazy). But opening and closing is a breeze and even all 6 indicators light up (one blink means close, 2 blinks is opened). 

Lastly, the OEM alarm interior light does not work with this receiver, maybe its to do with a voltage difference.
<img width="641" height="348" alt="image" src="https://github.com/user-attachments/assets/d22a6442-db20-427c-a71e-14da09a45b2d" />


## OTP Encoding
Now to be honest, I could have designed another receiver box/module that was rolling code and could communicate and pair with Golf MK6 key-fobs, therefore integrating the automatic roll-down/up windows function or even the interior ventilation gimmick. However i was very interested in messing with this simple protocol as an RF begginer's project, so maybe in the future something like this can be made since I preserved the PCB that came with the MK6 remote.

### What is OTP Encoding?

**OTP** stands for **One-Time Programmable**. In the context of the encoder, it means the microchip contains an internal non-volatile memory layer that is permanently burned during manufacturing at the semiconductor factory with a fixed, unchangeable **20-bit identification code**.

Older RF encoders (like the classic PT2262) required 8 to 12 physical hardware pins connected to solder jumpers or DIP switches on your PCB so you could manually set a binary address. OTP encoding eliminates all of that physical configuration. Therefore, I chose the EV1527 encoder for this project as its footprint is very small and is readily available.

[EV1527 Datasheet
](./docs/EV1527.PDF)

---

### The 20-Bit Address & Possible Combinations

Every time you press a button on an EV1527 keyfob, the chip transmits a 24-bit frame:
* **20 Bits:** Factory-programmed unique address ID
* **4 Bits:** Data bits corresponding to the 4 button inputs ($K_0, K_1, K_2, K_3$)

#### Mathematical Combinations:
$$\text{Total Address Combinations} = 2^{20} = 1,048,576$$

With over 1 million unique code combinations, the probability of your keyfob sharing the exact same address code with another device nearby is roughly 1 in 1.05 million.

---

### Why OTP Encoding is the Best Choice for the Keyfob

* **Saves Board Space & Cost:** Eliminating DIP switches or solder jumper banks drastically shrinks your PCB area—allowing you to fit the EV1527 easily on your compact $37 \times 23.4\text{ mm}$ layout.
* **Zero Serial Management During Assembly:** You don't have to program microcontrollers or keep track of serial numbers when soldering. Every EV1527 chip off the reel is guaranteed to have a different hardcoded address straight out of the box.
* **Universal Receiver Compatibility:** Modern RF receivers (like learning-code receivers) use a simple pairing button. You press "Learn" on the receiver, press your keyfob button once, and the receiver saves your unique 20-bit ID into its memory.

---

### No Crystal Needed: The Internal Oscillator & $R_{OSC}$

The EV1527 does not require a crystal oscillator, crystal load capacitors, or an external clock source.

* **Internal RC Oscillator:** The chip uses an integrated Resistor-Capacitor (RC) oscillator circuit on the silicon die.
* **Single Resistor Control:** To set the clock speed, you simply connect a single external resistor ($R_{OSC}$) between the `OSC` pin and `VCC` (typically $300\text{ k}\Omega$ to $430\text{ k}\Omega$, with $330\text{ k}\Omega$ being the standard for $433.92\text{ MHz}$ systems).
* **How It Works:** The resistance value of $R_{OSC}$ determines the charge/discharge rate of the internal oscillator, setting the timing pulse width ($T_w$) for the transmitted ASK radio signal.


## ASK Transmitting

## Schema Design


## PCB Design

## Breadboard Prototype

## Final Results

