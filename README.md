# WhatsApp Cloud API + n8n Auto-Reply

Dieses Projekt verbindet die WhatsApp Cloud API (Meta) mit n8n, um
eingehende WhatsApp-Nachrichten automatisch zu empfangen, zu verarbeiten
und zu beantworten.

## Features
- Empfang von WhatsApp-Nachrichten per Webhook
- Automatische Verarbeitung und Antwort (z. B. per KI)
- Versand der Antwort ueber die Meta Graph API
- Optional: E-Mail-Log/Benachrichtigung

## Voraussetzungen
- Meta Business Account + WhatsApp Cloud API
- Gultiges Access Token (z. B. `META_WA_TOKEN`)
- n8n Instanz mit aktivem Webhook

## Ablauf (High-Level)
1. WhatsApp sendet eine Nachricht an den Webhook.
2. n8n liest Absender und Inhalt aus.
3. Optional: KI generiert eine Antwort.
4. n8n sendet die Antwort an die Graph API.

## n8n Setup (Kurz)
1. Webhook-Node anlegen (POST).
2. Nachrichtendaten parsen (Code-Node).
3. Optional: AI/LLM-Node fuer Antwort.
4. HTTP Request-Node fuer Reply:
   - URL: `https://graph.facebook.com/v19.0/{PHONE_NUMBER_ID}/messages`
   - Header: `Authorization: Bearer $META_WA_TOKEN`
   - Body: `messaging_product`, `to`, `type`, `text`

## Umgebungsvariablen
- `META_WA_TOKEN` : WhatsApp Cloud API Access Token

## Fehlerbehebung
- OAuth Error 190: Token ungueltig oder abgelaufen.
  Erzeuge ein neues Token in der Meta App und pruefe Scopes.

## Lizenz
Proprietary / Internal
