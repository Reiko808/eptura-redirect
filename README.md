# eptura-redirect
Mithilfe dieses Repositorys soll per QR-Code scan eine direkte Verbindung zur APP oder dem AppStore bzw. PlayStore hergestellt werden.

Dieses Repository dient als Intermediär-Infrastruktur zur Reduktion von Medienbrüchen in der mobilen Asset-Provisionierung.

Eptura Engage Smart Redirect Bridge
1. Zweckbestimmung (Scope)
Bereitstellung einer zustandslosen Deferred-Deep-Linking-Logik. Das System fungiert als Gateway zwischen physischen QR-Triggerpunkten und den plattformspezifischen App-Applikationen von Eptura (ehemals Condeco). 
Es adressiert die mangelnde native Store-Redirection-Fähigkeit der mobilen Betriebssysteme bei der Verwendung statischer QR-Codes.

2. Funktionslogik (Technical Architecture)
Die index.html implementiert eine User-Agent-Heuristik zur Identifikation des Zielsystems (iOS vs. Android) und initiiert folgende Kette:
URI-Scheme-Trigger: Versuch des Aufrufs von epturaengage:// oder condeco:// zur direkten App-Invocierung.
Timeout-Monitoring: Überwachung des Browser-Fokus.
Fallback-Routing: Bedingte Weiterleitung an die entsprechenden Repositories (App Store/Google Play Store), falls die lokale Installation fehlt.

3. Konfiguration & Wartung
Anpassungen der Store-Identifier oder URI-Schemata erfolgen direkt in der config-Konstante innerhalb der index.html:
Parameter	        Beschreibung	                      Aktueller Wert (März 2026)
appStore	        Apple App Store ID	                id1565099537
playStore	        Google Play Store Package	          com.condecosoftware.condeco
schemes	          Registered Custom URI Schemes	      epturaengage://, condeco://

4. Deployment-Instruktion
Host: GitHub Pages (Public Repository).
Deployment-Pfad: Root-Verzeichnis (/).
Protokoll-Anforderung: HTTPS (obligatorisch zur Vermeidung von TLS-Mischinhalts-Blockaden bei Redirects).
