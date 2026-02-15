---
author: Roberto
date: 2013-12-03 17:20:17+00:00
draft: false
title: Arcade-Controller mit MAME
type: post
url: /arcade-controller-mit-mame/
categories:
- Fertige Projekte
tags:
- CNC
- Elektronik
- Holz
- Spielzeug
---

Endlich nähern wir uns der Fertigstellung unseres Arcadecontrollers für [MAME](https://mamedev.org). Aufgrund der aktuell grassierenden "Raspberri-Pi-itis" ergab sich noch eine Planänderung: Der Controller wird als Standalone-Gerät aufgebaut, und der Spielerechner in Form eines Raspis direkt ins Gehäuse integriert. Doch dazu später mehr. ;)<!-- more -->


### GEHÄUSE


Nach ersten Überlegungen ([Teil 1](/arcade-cabinet-mit-mame-1/), [Teil 2](/arcade-cabinet-mit-mame-2/), ... ) und dem Bau von Prototypen

[![IMG_1922_edit](/wp-content/uploads/2013/12/IMG_1922_edit-300x300.jpg)
](/wp-content/uploads/2013/02/konsole1.png)erfolgte nochmals eine Anpassung der Anordnung der Knöpfe auf dem Controller. Beim Arcadeshop finden wir die erforderlichen [Maße der verwendeten Knöpfe](https://www.arcadeshop.de/images/specs/arcade-pb-sl-data.gif) und [hier für die Joysticks.](https://www.arcadeshop.de/images/specs/arcade-joyst-c-mount.gif)

Außerdem wächst das Gehäuse nochmal auf 100x30cm, damit es mehr Ellenbogenfreiheit für Spieler 1 und 2 gibt und es erhält zudem eine um 5 Grad geneigte Oberseite. Dazu kommen links und rechts noch passende Seitenteile, damit er auch auf dem Couchtisch abgestellt, oder auf-den-Schoß genommen werden kann. Man könnte ihn aber auch später noch in ein Cabinet integrieren.
Nach den ersten Skizzen und insgesamt zwei gebauten Test-Prototypen für die Knopfanordnung ergibt sich dann folgender Entwurf ([DXF-Datei mit allen Maßen und Lochdurchmessern hier](/wp-content/uploads/2013/12/mame-complete.dxf)):

[![mame complete](/wp-content/uploads/2013/12/mame-complete-294x300.png)
](/wp-content/uploads/2013/12/mame-complete.png)Dann geht es auch schon ans Fräsen und Zuschneiden der Einzelteile:

[![IMG_1636](/wp-content/uploads/2013/10/IMG_1636-1024x680.jpg)
](/wp-content/uploads/2013/10/IMG_1636.jpg)

Lediglich die vordere und hintere Abdeckung musste ich einseitig auf der Tauchsäge im 5° Winkel anschneiden, der Rest fiel direkt aus unserer CNC-Fräse. ;)

Die Kanten der Teile wurden aus Komfortgründen noch auf der Tischoberfräse abgerundet. Um das frische und helle Aussehen des Holzes beizubehalten erfolgt dann die zweimalige Oberflächenbehandlung mit Osmo Hartwachsöl weiß-transparent, dann noch eine finale Schicht mit Osmo Hartwachsöl seidenmatt zum Versiegeln. Der Zusammenbau des Gehäuses geht dann recht zügig voran.

Hier noch mal schnell die Materialliste im Überblick, und dann geht es auch schon weiter im nächsten Kapitel:



	  * Holz 12mm Birke Multiplex, etwa 1m² --> 25 EUR
	  * 60 Fräsminuten auf der CNC-Fräse --> 30 EUR
	  * Abrunden der Kanten auf der Tischoberfräse und Oberflächenschliff --> 5 EUR
	  * Hartwachsöl --> 5 EUR
	  * Leim --> 1 EUR



### ELEKTRONIK


Nach der Fertigstellung des Gehäuses können die Joysticks und die vielen Knöpfe mitsamt ihrer Cherry-Mikroschalter montiert werden.

[![IMG_1906_edit](/wp-content/uploads/2013/12/IMG_1906_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1906_edit.jpg)

Dann geht es auch direkt an den Einbau der Steuerplatine und die Verkabelung der Einzelteile. Die Steuerplatine verfügt dabei über einen handelsüblichen PS/2-Ausgang und emuliert eine Tastatur. Die entsprechenden Eingänge "drücken" dann die passenden Tasten für die Standardbelegung in MAME. Ein USB-Adapter ist auch verfügbar (und hier verbaut), es ist aber mittlerweile auch eine Version mit direktem USB-Ausgang erhältlich. Darüber, welche Anschlussart mehr gleichzeitig gedrückte Knöpfe zulässt, gibt es eine intensive Diskussion, auf die ich hier aus Platzgründen nicht eingehen werde. ;)

[![IMG_1813_edit](/wp-content/uploads/2013/12/IMG_1813_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1813_edit.jpg)

Die Masse wird von Schalter zu Schalter durchgeschleift und über handelsübliche 6,3mm Flachsteckhülsen mit Abzweig befestigt. Die Signale werden als Einzeladern verlegt und dann mit der I-PAC Steuerplatine verbunden.

[![IMG_1812_edit](/wp-content/uploads/2013/12/IMG_1812_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1812_edit.jpg)

Wichtig ist vor allem, dass man sich etwas Mühe gibt, die Kabel sauber zu verlegen und gebündelt zu befestigen. Das erleichtert die spätere Wartung oder Fehlersuche enorm, und sieht nebenbei auch viel eleganter aus. Nach gefühlten Kilometern an Leitungen, unendlich vielen Adernend- und Flachsteckhülsen ist alles fertig verdrahtet. Der Raspberry Pi hat auch schon testweise seinen Platz gefunden. ;)

[![IMG_1811_edit](/wp-content/uploads/2013/12/IMG_1811_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1811_edit.jpg)

[![IMG_1919_edit](/wp-content/uploads/2013/12/IMG_1919_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1919_edit.jpg)

Hier noch die Materialaufstellung der benötigten Teile:



	  * I-PAC Steuerplatine --> 42 EUR
	  * 2 mal Joystick Competition Pro --> á 15 EUR
	  * 2 mal 8 Stück Pushbuttons in verschiedenen Farben --> á 2.20 EUR = 35,20 EUR
	  * Kabelsalat von Lapp in blau und schwarz --> 15 EUR
	  * 24 Kabelschuhe 6,3mm, 24 Kabelschuhe 6,3mm mit Abzweig, Adernendhülsen --> 10 EUR



### HARDWARE UND SOFTWARE


Um das Ganze jetzt noch mit Leben zu füllen, benötigt man noch einen Computer, auf dem der Emulator MAME läuft. Wie schon oben angesprochen integrieren wir einfach Steuerplatine und  Computer mit ins Gehäuse. Dafür greifen wir auf einen Raspberry Pi in der Version B zurück.

Der Vorteil dieser eleganten Lösung erschließt sich sogleich: Es gehen zur Stromversorgung nur noch ein USB-Kabel in den Controller hinein, und ein HDMI-Kabel mit Bild und Ton kommt heraus. Damit kann man den Controller auch mal leicht zu Freunden mitnehmen oder auch im Kombinat ganz entspannt auf der Couch zocken. Daher habe ich die nötigen Kabel gleich in einer Länge von 5m eingekauft. ;)

Man nehme also:



	  * einen Raspberry Pi Version B --> 35 EUR
	  * Gehäuse für den Raspberry Pi --> 5 EUR
	  * Sandisk Extreme 16GB SD-Karte --> 27 EUR
	  * USB-Netzteil, 2A --> 3 EUR
	  * Micro-USB Anschlusskabel, 5m --> 5 EUR
	  * HDMI-Kabel, 5m --> 5 EUR

Auf die SD-Karte spiele man dann das aktuelle [pimame-Image](https://pimame.org/), und natürlich Spiele, z.B. in Form von [ROM-Images frei verfügbarer Spiele](https://www.mamedev.org/roms/).

Um die letzten Leistungsreserven herauszukitzeln gibt es im pimame-Forum die Empfehlung, auf den Raspberry noch die passenden Kühlkörper aufzukleben und ihn moderat zu übertakten.
Folgende Einstellungen werden dabei empfohlen:

    
    /boot/config.txt
    
    arm_freq=900
    core_freq=300
    sdram_freq=500


Vorsicht, hier gefährdet ihr unter Umständen Eure Gewährleistung. Ich habe daher vorerst auf das Übertakten verzichtet.

Der auf der pimame-Distribution enthaltene Mame4All-Emulator ist bereits für schwächere Rechner optimiert. Die zugehörigen Roms sind noch diejenigen der Version 0.37b5 oder 0.37b11 (während ein aktuelles Mame auf leistungsstärkeren Rechnern längst bei Version 0.150 angekommen ist).

Hinweis: Da ein Controller normalerweise über keine Tasten für ENTER, ESC oder TAB verfügt, hat die I-PAC-Platine auch eine sogenannte "Shift"-Funktion, um diese, zum Starten oder Beenden von Spielen notwendigen Tasten, trotzdem bereitzustellen. Hier nochmal die wichtigsten Tastenkombinationen Überblick:

    
     START1 + START2 == ESC
     START1 + LINKS  == ENTER
     START1 + RECHTS == TAB
     START1 + UNTEN  == PAUSE


Die komplette Aufstellung der Tastenkürzel für die I-PAC-Platine findet ihr auch [auf der Webseite von Ultimarc](https://www.ultimarc.com/control-interfaces/i-pacs/i-pac2/).


### ERGEBNIS


Fertig! Jetzt geht's erstmal ans Zocken und Genießen.

[![IMG_1918_edit](/wp-content/uploads/2013/12/IMG_1918_edit-1024x680.jpg)
](/wp-content/uploads/2013/12/IMG_1918_edit.jpg)Wer sich den Controller mal live anschauen möchte ist natürlich herzlich eingeladen, dies z.B. an einem Samstag [während der Öffnungszeiten](/oeffnungszeiten/) zu tun.

Wer hingegen noch Anregungen für einen eigenen Controller oder ein komplettes Cabinet benötigt, findet hier als Anregung [eine Webseite mit vielen Bildern und Informationen rund um's Thema](https://wiki.laub-home.de/wiki/Projekt_Arcade_Cabinet).
