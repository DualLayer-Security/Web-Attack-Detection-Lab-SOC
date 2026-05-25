# 🛡️ Web Attack Detection Lab (SOC Incident Analysis)

## 📌 Overview

Este laboratorio simula un escenario real de un **Security Operations Center (SOC)**, donde se analiza tráfico malicioso dirigido a un servidor web Apache.

El objetivo es detectar, analizar, correlacionar y responder a actividad sospechosa utilizando logs del sistema.

---

## 🧱 Environment

| Component | Role |
|----------|------|
| Ubuntu Server | Web Server (Apache2) |
| Kali Linux | Traffic Generator |

---

## ⚙️ System Setup

Servidor Apache desplegado en Ubuntu.

![Apache Running](./01-Apache-Srvice-Running.png)

---

## 🌐 Network Configuration

IP del servidor Ubuntu.

![Ubuntu IP](./02-IP-Ubuntu.png)

---

## 🌍 Web Access Validation

Acceso al servidor desde Kali.

![Web Access](./03-Web-Access-From-Kali.png)

---

## 📂 Endpoint Validation

Validación de endpoints web:

- /admin  
- /login  
- /test  

![Endpoints](./04-Web-Endpoints-Validation.png)

---

## 🔍 Traffic Generation

Peticiones HTTP manuales con curl.

![Curl Requests](./05-Manual-Curl-Requests.png)

---

## 📡 Detection Phase

### 🔵 Real-Time Monitoring

```bash
tail -f /var/log/apache2/access.log
```

![Realtime Logs](./06-Realtime-Access-Logs.png)

---

### 🟡 Fuzzing Detection

Actividad automatizada detectada en logs.

![Fuzzing](./07-Fuzzing-Logs-Detected.png)

---

### 🔴 SQL Injection Attempt

Detección de payload en logs.

![SQLi](./08-Sqli-Log-Entry.png)

---

### 🔴 Path Traversal Attempt

Intento de acceso a archivos del sistema.

![Traversal](./09-Path-Traversal-Log-Entry.png)

---

## 🧠 Analysis Phase

### 📊 Pattern Analysis

Clasificación de actividad en logs.

![Analysis](./10-Logs-Clasification-Admin.png)

---

### 🧩 Attack Correlation

Secuencia completa del ataque.

![Timeline](./11-Full-Timeline-Correlation.png)

---

## 🚨 Response Phase

### 🛑 IP Blocking

```bash
sudo iptables -A INPUT -s <ATTACKER_IP> -j DROP
```

![Firewall](./12-Firewall-IP-Block-Rule.png)

---

### 🔒 Block Validation

Verificación desde Kali.

![Blocked](./13-Attack-Blocked-Validation.png)

---

### 📊 Post-Mitigation

Validación de tráfico tras bloqueo.

![Post](./14-Post-Mitigation-Traffic-Validation.png)

---

## 📊 Findings

- Reconocimiento de endpoints detectado
- Fuzzing automatizado identificado
- Intentos de SQL Injection
- Intentos de Path Traversal
- Correlación de eventos
- Respuesta mediante firewall

---

## 🧠 Conclusions

El tráfico analizado corresponde a un ataque web en múltiples fases:

1. Reconocimiento  
2. Enumeración  
3. Intentos de explotación  

---

## 🛡️ Recommendations

- Implementar WAF
- Integrar SIEM (Wazuh / ELK)
- Alertas por volumen de tráfico
- Uso de Fail2ban
- Mejora de monitorización
