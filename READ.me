# 🏋️ Training Tracker System

Ein intelligentes Fitness-Tracking-System mit Event-driven Architecture, das Training, Schlaf und Aktivitätsdaten in einer Graph-Datenbank verbindet.

## 📋 Inhaltsverzeichnis

- [Features](#features)
- [Tech Stack](#tech-stack)
- [Architektur](#architektur)
- [Installation](#installation)
- [Workflows](#workflows)
- [Verwendung](#verwendung)
- [Neo4j Schema](#neo4j-schema)
- [Beispiele](#beispiele)

---

## ✨ Features

### 🎯 Core Features
- ✅ **Trainingszyklus-Management** - Erstelle Trainingspläne über natürliche Sprache
- ✅ **Interaktives Training-Logging** - Force-Reply basiertes Training mit Progressive Overload
- ✅ **Polar Flow Integration** - Automatischer Import von Sleep & Activity Daten via Webhook
- ✅ **Progressive Overload Tracking** - Zeigt automatisch letzte Performance
- ✅ **Graph-basierte Datenstruktur** - Ermöglicht komplexe Abfragen

### 📊 Datenerfassung
- Trainingseinheiten mit detaillierten Satz/Wiederholungs-Daten
- Schlafanalyse (Tiefschlaf, REM, HRV, Sleep Score)
- Tägliche Aktivität (Schritte, Kalorien, Distanz)

---

## 🛠 Tech Stack

- **n8n** - Workflow Automation
- **Neo4j** - Graph Database
- **Telegram** - User Interface
- **OpenAI GPT-4** - Natural Language Processing
- **Polar Flow API** - Health Data Integration

---

## 🏗 Architektur

```
┌─────────────┐
│  Telegram   │ ← User Interface
└──────┬──────┘
       │
┌──────▼──────┐
│     n8n     │ ← Workflow Engine
└──────┬──────┘
       │
       ├──────► OpenAI (NLP)
       ├──────► Polar API (Webhooks)
       ▼
┌─────────────┐
│   Neo4j     │ ← Graph Database
└─────────────┘
```

---

## 📦 Installation

### Voraussetzungen

- Docker & Docker Compose
- n8n Instance
- Neo4j Database (v5+)
- Telegram Bot Token
- OpenAI API Key
- Polar Flow API Access

### 1. Neo4j Setup

```bash
docker run -d \
  --name neo4j \
  -p 7474:7474 -p 7687:7687 \
  -e NEO4J_AUTH=neo4j/your-password \
  neo4j:latest
```

**Constraints erstellen** (Neo4j Browser → http://localhost:7474):

```cypher
CREATE CONSTRAINT trainingszyklus_id IF NOT EXISTS 
FOR (tz:Trainingszyklus) REQUIRE tz.id IS UNIQUE;

CREATE CONSTRAINT trainingstag_id IF NOT EXISTS 
FOR (tt:Trainingstag) REQUIRE tt.id IS UNIQUE;

CREATE CONSTRAINT übung_name IF NOT EXISTS 
FOR (ue:Übung) REQUIRE ue.name IS UNIQUE;
```

### 2. n8n Setup

```bash
docker run -d \
  --name n8n \
  -p 5678:5678 \
  -e WEBHOOK_URL=https://your-domain.com \
  n8nio/n8n:latest
```

**Credentials konfigurieren:**
- Telegram Bot Token (von @BotFather)
- OpenAI API Key
- Neo4j Connection
- Polar Flow OAuth2

### 3. Workflows importieren

1. `workflow-trainingszyklus-erstellen.json`
2. `workflow-training-interactive.json`
3. `workflow-polar-sync.json`

### 4. Polar Flow Webhook

URL: `https://your-domain.com/webhook/polar_health_data`  
Event: `SLEEP`

---

## 🔄 Workflows

### 1️⃣ Trainingszyklus erstellen

**Trigger:** Telegram Message

```
Telegram → OpenAI → Neo4j → Telegram
```

**Input Beispiel:**
```
Neuer Zyklus "Hypertrophie" für 8 Wochen.

Montag:
- Bankdrücken 4 Sätze
- Schrägbankdrücken 3 Sätze
```

---

### 2️⃣ Training Interactive Session

**Trigger:** `/training`

```
/training → Loop über Übungen → Speichern → Zusammenfassung
```

**Features:**
- Zeigt letzte Performance
- Force Reply Eingabe
- Progressive Overload

---

### 3️⃣ Polar Flow Sync

**Trigger:** Webhook (SLEEP Event)

```
Webhook → API Calls → Transform → Neo4j
```

**Output:**
- Activity + Sleep Daten am Tag-Node

---

## 📖 Verwendung

### Trainingszyklus erstellen

```
Ich möchte einen Trainings Cycle von 12 Wochen.

Montag
- Pull Ups 5 Sätze
- Dips 3 Sätze
```

### Training loggen

```
/training
```

Bot fragt nach jeder Übung, du antwortest mit Wiederholungen:
```
10, 10, 9, 8
```

---

## 🗺 Neo4j Schema

### Hauptstrukturen

```
(Trainingszyklus)-[:HAT_TRAININGSTAG]->(Trainingstag)
(Trainingstag)-[:ENTHÄLT]->(GeplantÜbung)-[:IST]->(Übung)

(Tag)-[:HATTE_TRAINING]->(Trainingseinheit)
(Tag)-[:HATTE_AKTIVITÄT]->(Activity)
(Tag)-[:HATTE_SCHLAF]->(Sleep)

(Trainingseinheit)-[:BESTEHT_AUS]->(AusgeführteÜbung)
(AusgeführteÜbung)-[:IST_TYP]->(Übung)
```

### Beispiel-Query

```cypher
// Trainingsfortschritt einer Übung
MATCH (ue:Übung {name: "Pull Ups"})<-[:IST_TYP]-(ao)
      <-[:BESTEHT_AUS]-(te:Trainingseinheit)
RETURN te.datum, ao.wiederholungen
ORDER BY te.datum DESC
```

---

## 💡 Beispiele

### Progressive Overload

**Woche 1:** `10, 10, 9, 8, 7`  
**Woche 2:** Bot zeigt: `📊 Letztes Mal: 5 Sätze: 10, 10, 9, 8, 7`  
**Du gibst:** `10, 10, 10, 9, 8` → Fortschritt!

### Korrelation Sleep ↔ Training

```cypher
MATCH (t:Tag)-[:HATTE_SCHLAF]->(s:Sleep)
MATCH (t)-[:HATTE_TRAINING]->(te)
WHERE s.schlafwert >= 80
RETURN te.datum, s.schlafwert, te.gesamte_sätze
```

---
