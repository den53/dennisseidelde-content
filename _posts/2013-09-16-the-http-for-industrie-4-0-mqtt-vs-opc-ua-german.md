---
ID: 982
post_title: 'MQTT vs OPC-UA: Das HTTP der Industrie 4.0?'
author: Dennis
post_date: 2013-09-16 10:48:19
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/the-http-for-industrie-4-0-mqtt-vs-opc-ua-german/
published: true
image:
  - ""
mfn-post-love:
  - "1"
dsq_thread_id:
  - "3429460863"
---
<h2><span style="font-family: Tahoma; font-size: 17px;">WebSphere Message Broker(MQTT) vs OPC-UA</span></h2>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">OPC-UA und MQTT sind M2M Kommunikationsprotolle. OPC entwickelte sich aus einem ojektorientierten Remote Procedure Call System heraus (DOM/CDOM), welches in OPC-UA durch ein eigenes verbessertes System ersetzt wurde.</span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Der Open Source Standard MQTT entwickelte sich aus WebSphere MQ. MQTT ist ein extrem einfaches und leichtgewichtiges publish/subscribe Messaging system. MQTT wurde für niedrige Bandbreite mit hoher Latenz und unzuverlässige Netwerken designt. OPC-UA wurde in der neusten Version weiter ausgebaut um nicht nur Maschinendaten (Prozesswerte, Messwerte, Parameter usw.) zu transportieren, sondern auch maschinenlesbare Daten semantisch zu beschreiben.</span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Die MQTT Entwicklung ist stark durch die Erfahrungen der IT Industrie geprägt. OPC-UA hingegen fokussiert sich auf die Domain-Anforderungen der Industrie und weniger auf technische höchste Leistungsfähigkeit und Flexibilität. </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>

<h2 style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Datenkommunikation</span></h2>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Der WebSphere Message Broker (WSMB)(MQTT) und OPC-UA nutzen auf der Netzwerkebene TCP/IP, wobei MQTT auch Sockets unterstützt. Auf der Transportebene unterstützen beide Protokolle TCP (binary). WSMB unterstützt weiter TCP (any) und UDP (any). Auf der Applikationsebene unterstützen beide HTTP (WebServices), WSMB versteht weiter MQ, MQTT und JMS. </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">OPC-UA kann nur unidirektionale (Client to Server) Kommunikation. Wenn ein Server Daten benötig, muss er auch einen Client implementieren. WSMS/MQTT unterstützt weiter bidirektional Kommunikation und hebt damit diese Limitierung auf.  OPC-UA ist auf Punkt-zu-Punkt Kommunikation beschränkt. WSMB/MQTT bietet zusätzlich Publish/Subscribe und ESB managed Kommunikation (ESB Routing). Daher werden bei OPC-UA die Subscriptions über Requests abgeholt. OPC-UA braucht sehr viele Schritte für den initialen Verbindungsaufbau und Auslesen der Konfigurationen. Insgesamt ist der Kommunikation-Overhead bei OPC-UA groß. WSMB/MQTT besitzt neben einem leichteren Protokoll auch Transaktionalität im Protokoll von MQ, MQTT, JMS bis hin zu SOAP. </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>

<h2 style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Datenformat</span></h2>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Die Stärke von OPC-UA ist sein hierarchisches Objektmodell mit (bidirektionalen) Verbindungen zwischen Objekten (auf verschiedenen Servern). Wobei mögliche zyklische Abhängigkeiten von Programmierer selbst ausgeschlossen werden müssen.</span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">WSMB/MQTT kann prinzipiell jedes Format abbilden. Dies bietet weitere Flexibilität, erfordert aber mehr Entwicklungsarbeit da Objekt-Relationen nur bedingt out-of-the-box vorhanden sind.</span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Beide Objektmodell und das darauf aufbauende Zugriffsmodell von OPC und MQTT sind generisch und müssen durch passende Industriestandards gefüllt werden. </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>

<h2 style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Implementierung</span></h2>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Die offenen Referenzimplementierung von OPC ist in C#. Weiter gibt es offene Implementierungen in Java und in embedded Systems (z.B. durch das  Frauenhofer Institut). Die Erfahrung zeigt, dass der Aufwand (je nach benötigtem Funktionsumfang) überschaubar ist.</span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Die offene Referenzimplementierung von MQTT gibt es in verschiedenen Sprachen. Am verbreitetsten sind Java und C. Insgesamt bietet MQTT die leichtgewichtigste Implementierung mit dem geringsten Kommunikationsoverhead. </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>

<h2 style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Zusammenfassung</span></h2>
<p style="margin: 0px; font-size: 12px; font-family: Arial; min-height: 14px;"><span style="font-family: Tahoma; font-size: 17px;"> </span></p>
<p style="margin: 0px; font-size: 12px; font-family: Arial;"><span style="font-family: Tahoma; font-size: 17px;">Der Kernunterschied zwischen OPC und MQTT ist der Blickwinkel. MQTT bietet Lösungen für die Herausforderungen von niedriger Bandbreite mit hoher Latenz und lässt den Rest flexibel erweiterbar. OPC-UA liefert bereits Domainwissen durch ein hierarchisches Objektmodell out-of-the-box.</span></p>