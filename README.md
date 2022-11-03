## Tilraunir með RPi, GPIO og Picam 

- RPi 
- GPIO
- PiCam
- Vefþjónusta

---

#### Uppsetning á RPi stýrikerfi (sleppa)

Settu upp RPi stýrikerfi á SD minniskortið þitt og stilltu RPi Zero skv. [leiðbeiningum](https://github.com/VESM3/IOT/blob/main/Efni/RPiuppsetning.md) þannig að þú getur tengst wifi bæði heima og í skóla.

---

#### 1. Thonny ritill. 
Notaðu [Thonny](https://thonny.org/) ritil á RPi OS. Búðu til python skrá og prentaðu út strenginn með nafninu þínu, sjá nánar [Get Started with Thonny IDE on Raspberry Pi OS](https://roboticsbackend.com/thonny-ide-raspberry-pi-os/).

---

#### 2. Nano ritill í terminal. (sleppa)
Notaðu terminal og Linux skipanir til að skoða þig um í RPi stýrikerfinu. Búðu til python skrá og notaðu [nano](https://www.nano-editor.org/) command-line ritil í terminal til að skrifa python kóða sem innheldur prentskipun með nafninu þínu. Keyrðu svo python skránna í terminal. sjá [Raspberry Pi – Run Python Script in the Terminal](https://roboticsbackend.com/raspberry-pi-run-python-script-in-the-terminal/).

---

#### 3. GPIO: Blikkandi ljós. 
Láttu LED blikka á brauðbretti með python kóða. Notaðu [T-Coppler](https://www.adafruit.com/product/2028) með brauðbrettinu og [GPIO Zero](https://gpiozero.readthedocs.io/en/stable/) python safnið með kóðalausn. Nýttu þér kóðalausnir í [Basic Recipes](https://gpiozero.readthedocs.io/en/stable/recipes.html). Hér er [GPIO Zero pinout](https://gpiozero.readthedocs.io/en/stable/cli_tools.html#pinout) þegar þú notar ekki T-Coppler.

---

#### 4. GPIO: Takki og LED. (10%)
Við að ýta á takka þá kemur birta af LED. 

---

### 5. PiCamera 
1. Taktu mynd af þér með að nota terminal
   - **Varúð!** Slökktu fyrst á RPi þegar þú tengir myndavélina við Camera Serial Interface (CSI) á RPi. 
   - Tengdu PiCamera við RPi. Ef þú ert að nota RPi Zero þá sjá hér [How to connect a Picamera to a Pi ZERO (myndband)](https://www.youtube.com/watch?v=zFAX4pH1BPA). 
   - Fylgdu [Getting started with the Camera Module](https://projects.raspberrypi.org/en/projects/getting-started-with-picamera/2)
   - [Picamera Documentation](https://www.raspberrypi.com/documentation/accessories/camera.html#hardware-specification)
1. Skrifaðu python kóða til að takta mynd með 1024x768 upplausn af sjálfum þér með Pi V2 myndavélinni tengda við RPi og vistaðu á skjáborðinu. `camera.capture('/home/pi/Desktop/image.jpg')` 
   - [picamera library](https://picamera.readthedocs.io/en/release-1.13/)
1. Ath. RPi Zero virkar ekki vel með [libcamera](https://www.raspberrypi.com/documentation/accessories/camera.html).

---

### 6. Að taka ljósmynd með takka.
1. Notaðu takka (þegar honum er sleppt) til að taka myndina.
1. Bættu við 3 sek. timer með takka til þess að taka myndina, [Button controlled camera](https://gpiozero.readthedocs.io/en/stable/recipes.html#button-controlled-camera)

---


#### 7. PIR hreyfiskynjarinn. 
Kynntu þér PIR og notaðu hreyfisyknjara til að kveikja á LED. 

- [PIR (lastminute)](https://lastminuteengineers.com/pir-sensor-arduino-tutorial/)
   - PIR er tengt í 5V (er með innbyggðan 3.3V regulator) 
   - Víxlaðu GND og Vc staðsetningum (mismunandi eftir tegundum).
   - stilltu næmleika og timeout á PIR með að snúa báðum allaleið rangsælis.
   - taktu linsu af PIR til að þrengja IR svið. 
- [PIR (adafruit)](https://learn.adafruit.com/pir-passive-infrared-proximity-motion-sensor/overview)
- [Motion sensor kóðalausn](https://gpiozero.readthedocs.io/en/stable/recipes.html#motion-sensor)

---

#### 8. PIR og PiCamera.

1. Taktu mynd þegar PIR hreyfiskynjari fer í gang  
1. Sendu ljósmyndina á gmail netfang.
    - [How to Use the Raspberry Pi4 Camera and PIR Sensor to Send Emails](https://maker.pro/raspberry-pi/projects/how-to-use-the-raspberry-pi4-camera-and-pir-sensor-to-send-emails)
    - Búðu til Gmail reikning og leyfðu “Allow less secure apps” svo hægt er að taka við tölvpóst með python kóða.
    - Slepptu að nota buzzer
    
---


### 9. Myndbandsupptaka 
Með PiCam og RPi er hægt að taka upp og streyma myndbönd. Taktu upp stutt myndband með PiCam. Sjá t.d. [Video to file](https://picamera.readthedocs.io/en/release-1.10/recipes1.html#recording-video-to-a-file).
**Skoða** Settu upp myndbandsstreymi, hýstu á vefsíðu með ESP32 eða notaðu VLC. [sýnidæmi 1](https://github.com/miguelgrinberg/flask-video-streaming), [sýnidæmi 2](https://www.tomshardware.com/how-to/stream-live-video-raspberry-pi)

---

### 10. Myndgreining með vefþjónustu

[Myndgreiningavefþjónustur](https://nordicapis.com/7-best-image-recognition-apis/) eru sniðugar til að greina hluti, andlit, liti og texta á ljósmyndum.

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

Gott að vita: RPi Zero virkar ekki með með OpenCV

---

Takk fyrir daginn!

kv Gunnar og Eiríkur.
