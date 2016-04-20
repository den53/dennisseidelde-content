---
ID: 1014
post_title: 'MQTT &#8211; Eine Einführung'
author: Dennis
post_date: 2013-08-25 20:24:16
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/mqtt-eine-einfuhrung/
published: true
image:
  - ""
mfn-post-love:
  - "0"
slide_template:
  - ""
dsq_thread_id:
  - "3425628314"
---
<p><span style="font-family: Tahoma; font-size: 17px;">Message Queuing Telemetry Transport (MQTT) ist ein äußerst simpel aufgebautes Publish-Subscribe-Protokoll für den Nachrichtenaustausch zwischen Geräten geringer Funktionalität. Das robuste MQTT-Protokoll wurde für unzuverlässige Netze mit geringer Bandbreite und hoher Latenzzeit entwickelt. MQTT minimiert die genutzte Netzwerk-Bandbreite und die Anforderungen an Geräte , gleichzeitig wird für die Datenübermittlung eine hohe Zuverlässigkeit erreicht. Diese Anforderungen bestehen insbesondere bei Sensornetzwerken, bei Machine to Machine(M2M), in der Telemedizin, der Patientenüberwachung und beim "Internet der Dinge". Bei dieser Anwendung sind die angeschlossenen Geräte "Always On" und kommunizieren ständig miteinander.</span></p>
<p><span style="font-family: Tahoma; font-size: 17px;">Das offene, lizenzfreie MQTT-Protokoll wurde bereits 1999 von IBM für die Satellitenkommunikation entwickelt und später in vielen industriellen Anwendungen eingesetzt. Es ist äußerst einfach zu implementieren, kennt drei unterschiedliche Dienstgüten (QoS) für Service-Optionen und kann ununterbrochen Sitzungen mit den festen und mobilen Geräten betreiben.</span></p>
<p><span style="font-family: Tahoma; font-size: 17px;">Seit 2013 standardisiert die OASIS MQTT als Protokoll des Internet der Dinge. Das MQTT-Protokoll ist auch bekannt als SCADA-Protokoll und WebSphere MQTT" (WMQTT). Die Internet Assigned Numbers Authority (IANA) reserviert für MQTT die Ports 1883 und 8883. Um die Sicherheit der Nachrichtenübermittlung zu gewährleisten, kann der Benutzer seinen Namen und sein Passwort in einem MQTT-Paket übertragen. Außerdem können die Nachrichten mit dem SSL-Protokoll verschlüsselt werden.</span></p>
<p><span style="font-size: 17px;">Die Struktur in der das MQTT-Protokoll arbeitet, besteht aus der Datenquelle, die als Publisher bezeichnet wird, der Datensenke, dem Subscriber, und dem zwischengeschalteten Message-Broker, der für die Kommunikationssteuerung sorgt. Die Grafik stellt beispielhaft die MQTT Topologie dar.</span></p>
<p><span style="font-size: 17px;"><img class="alignnone" src="http://imageshack.us/a/img42/1123/z2w.gif" alt="MQTT Topologie" width="558" height="355" /></span></p>
<p><span style="font-size: 17px;">Im Kontext von Industrie 4.0 ist MQTT/MessageBroker neben OPC-UA eine Option um die Vernetzung zwischen Artefakten der modernen Fabrik zu ermöglichen. Lesen Sie in kürze den Vergleich zwischen MQTT vs OPC-UA.</span></p>