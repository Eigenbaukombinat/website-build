---
author: marian
date: 2013-11-06 12:52:34+00:00
draft: false
title: Straßenbahn-Abfahrtsanzeige mit einem Raspberry Pi
type: post
url: /strasenbahn-abfahrtsanzeige-mit-einem-raspberry-pi/
categories:
- Fertige Projekte
tags:
- Elektronik
---

In unserem [neuen großen Raum](/wir-bauen-aus-das-eigenbaukombinat-bald-auf-230m%C2%B2/), der unter anderem als Sozialraum bzw. Treffpunkt dient, fehlte eine Uhr. Ich kam auf die Idee, auch gleich die ausgehängten Papierfahrpläne unnötig zu machen und eine Anzeige zu entwickeln, die neben der aktuellen Uhrzeit zusätzlich die nächsten Bahnen ab der Haltestelle Lutherstraße (etwa 3 Minuten zu Fuß vom Eigenbaukombinat) anzeigt.

<!-- more -->

Leider bietet die [HAVAG](https://havag.com) bzw. der [MDV](https://mdv.de) keine offizielle Schnittstelle an, mit der man auf die Daten zugreifen könnte. Ich musste daher eine andere Lösung suchen und verfiel auf die Fahrplanauskunft.

Jede Minute werden von der Webseite des [NASA](https://nasa.de/) (gemeint ist hier der Nahverkehrsservice Sachsen-Anhalt) die aktuellen Abfahrten mit Echtzeitdaten abgefragt. Leider ist die Datenqualität ziemlich schlecht, so fehlen regelmäßig Bahnen, andere scheinen nur mit ihrer Planzeit auf (keine Echtzeitdaten).

Wie man als leidgeprüfter Bahnfahrer weiß, sind außerdem die Daten bei größeren Störungen nicht zu gebrauchen - da die Anzeigen der HAVAG in solchen Fällen auch nur Mist anzeigen, ist das wohl ein Fall von "garbage in, garbage out".

Das Programm läuft auf einem [Raspberry Pi](https://www.raspberrypi.org/), einem Einplatinencomputer, der für etwa 35 Euro zu haben ist. Als Betriebssystem habe ich [Raspbian](https://www.raspberrypi.com/software/) gewählt, ein Debian-Derivat, das auf den Raspberry Pi zugeschnitten ist.

[![raspi](/wp-content/uploads/2013/11/raspi-300x251.jpg)
](/wp-content/uploads/2013/11/raspi.jpg).

Und so sieht die Anzeige fertig montiert aus, die Kabelführung wird noch verbessert:

[![anzeige](/wp-content/uploads/2013/11/anzeige-300x225.jpg)
](/wp-content/uploads/2013/11/anzeige.jpg)

Der Sourcecode ist bei [GitHub](/github.com/Eigenbaukombinat/pynasa) zu finden.
