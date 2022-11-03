## Tilraunir með RPi

- RPi 
- GPIO
- PiCam
- Skynjarar
- Vefþjónusta

---

#### Uppsetning á RPi stýrikerfi (sleppa, búið að gera)

Settu upp RPi stýrikerfi á SD minniskortið þitt og stilltu RPi Zero skv. [leiðbeiningum](https://github.com/VESM3/IOT/blob/main/Efni/RPiuppsetning.md) þannig að þú getur tengst wifi bæði heima og í skóla.

---

#### 1. Thonny ritill. 
Notaðu [Thonny](https://thonny.org/) ritil á RPi OS. Búðu til python skrá og prentaðu út strenginn með nafninu þínu, sjá nánar [Get Started with Thonny IDE on Raspberry Pi OS](https://roboticsbackend.com/thonny-ide-raspberry-pi-os/).

---

#### 2. Nano ritill í terminal. (sleppa)
Búðu til python skrá og notaðu [nano](https://www.nano-editor.org/) command-line ritil í terminal til að skrifa python kóða sem innheldur prentskipun með nafninu þínu. Keyrðu svo python skránna í terminal. sjá [Raspberry Pi – Run Python Script in the Terminal](https://roboticsbackend.com/raspberry-pi-run-python-script-in-the-terminal/).

---

#### 3. GPIO: Blikkandi ljós. 
Láttu LED blikka á brauðbretti með python kóða. Notaðu [T-Coppler](https://www.adafruit.com/product/2028) með brauðbrettinu og `GPIO Zero` safninu. Nýttu þér kóðalausnir í [Basic Recipes](https://gpiozero.readthedocs.io/en/stable/recipes.html). Hér er [GPIO Zero pinout](https://gpiozero.readthedocs.io/en/stable/cli_tools.html#pinout) þegar þú notar ekki T-Coppler.

Pæling. hvað ætli `pause()` skipunin geri?

---

#### 4. GPIO: Takki og LED. 
Við að ýta á takka þá kemur birta af LED. 

Pæling: Hver er munurinn á `when_pressed`, `is_pressed` og `wait_for_press`?

---

#### 5. PiCamera V2
Það þarf að nota Debian Buster 32-bit (legacy) RPi stýrikerfið til að geta notað PiCamera V2. Hér er nánar um 
[Picamera V2 hardware](https://www.raspberrypi.com/documentation/accessories/camera.html#hardware-specification)

Fylgdu [Getting started with the Camera Module](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/2) tutorial og skoðaðu [picamera](https://picamera.readthedocs.io/en/release-1.13/recipes1.html#) safnið.
1. Slökktu fyrst á RPi þegar þú tengir myndavélina við Camera Serial Interface (CSI) á RPi. 
   - Leiðbeiningar fyrir [RPi Zero](https://www.youtube.com/watch?v=zFAX4pH1BPA). 
1. Taktu mynd af þér með að nota terminal.
1. Skrifaðu python kóða til að takta mynd með 1024x768 upplausn af sjálfum þér með einhverjum effect með PiCam og vistaðu á skjáborðinu. `camera.capture('/home/pi/Desktop/image.jpg')`. 
1. Taktu upp stutt myndband með PiCam. Tvismelltu á skránna hún mun opnast í VLC spilara.


**Ath:** RPi Zero virkar ekki vel með [libcamera](https://www.raspberrypi.com/documentation/accessories/camera.html).

<!-- 
`omxplayer video.h264` 
[Get Started with Pi Camera V2](https://littlebirdelectronics.com.au/guides/198/get-started-with-pi-camera-v2) 
-->

---

#### 6. Streyma myndband (sleppa)
Með PiCam og RPi er hægt að streyma "live" myndbönd.  

- [sýnidæmi með VLC](https://www.tomshardware.com/how-to/stream-live-video-raspberry-pi)
- [sýnidæmi með Flask](https://github.com/miguelgrinberg/flask-video-streaming)

---

#### 7. Að taka ljósmynd með takka.
1. Notaðu takka (þegar honum er sleppt) til að taka ljósmyndina.
1. Bættu við 3 sek. timer með takka til þess að taka myndina, [Button controlled camera](https://gpiozero.readthedocs.io/en/stable/recipes.html#button-controlled-camera)

---


#### 8. PIR hreyfiskynjarinn. 
Kynntu þér PIR og notaðu hreyfisykynjara til að kveikja á LED. 

- [PIR (lastminute)](https://lastminuteengineers.com/pir-sensor-arduino-tutorial/)
   - PIR er tengt í 5V (er með innbyggðan 3.3V regulator) 
   - taktu linsu af PIR til að þrengja IR svið. 
   - Skoðaðu vel GND og Vc staðsetningar (mismunandi eftir tegundum)
   - stilltu næmleika og timeout á PIR eftir þörfum.
- [Motion sensor kóðalausn](https://gpiozero.readthedocs.io/en/stable/recipes.html#motion-sensor)

<!-- 
 [PIR (adafruit)](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/overview)
-->

---

#### 9. PIR og PiCamera.

1. Taktu mynd þegar PIR hreyfiskynjari fer í gang  
1. Sendu ljósmyndina á gmail netfang. (má sleppa)
    - [How to Use the Raspberry Pi4 Camera and PIR Sensor to Send Emails](https://maker.pro/raspberry-pi/projects/how-to-use-the-raspberry-pi4-camera-and-pir-sensor-to-send-emails)
    - Búðu til Gmail reikning og leyfðu “Allow less secure apps” svo hægt er að taka við tölvpóst með python kóða.
    - Slepptu að nota buzzer
    
---

#### 10. Myndgreining með vefþjónustu

[Myndgreiningavefþjónustur](https://nordicapis.com/7-best-image-recognition-apis/) eru sniðugar til að greina hluti, andlit, liti og texta á ljósmyndum.

Veldu þér þjónustu til að nota með RPi og PiCam.

<!--
Skoðaðu og notaðu [Computer Vision](https://azure.microsoft.com/en-us/services/cognitive-services/computer-vision/#overview) frá Microsoft Azure til að greina hluti á ljósmynd. 

1. Myndgreining með Computer Vision
   1. Búðu til aðgang hjá Azure via _`Github Student Developer Pack`_ (gætir þurft að skrá þig út á Azure)
   1. Gerðu viðeigandi stillingar hjá Azure til að geta notað Computer Vision. 
   1. Notaðu VSCode og python á fartölvunni, ([kóðadæmi](https://github.com/VESM3/IOT/blob/main/Efni/ComputerVisionDemo.py)) til að greina ljósmynd (minna en 4MB).
1. Notaðu RPi, PiCam og Computer Vision saman og birtu niðurstöður. 

**Bjargir**
- [Computer Vision with Microsoft Azure](https://www.pluralsight.com/guides/computer-vision-with-microsoft-azure)
- [Computer Vision documentation](https://docs.microsoft.com/en-us/azure/cognitive-services/computer-vision/)
- [Computer Vision SDK for Python](https://docs.microsoft.com/en-us/python/api/overview/azure/cognitiveservices-vision-computervision-readme?view=azure-python-preview)
- [myndbönd](https://www.youtube.com/hashtag/azureinpython)

-->

- Gott að vita: RPi Zero virkar ekki með með OpenCV

---

Takk fyrir!

kv. Eiríkur og Gunnar
