# SIEM-Splunk-BruteForce-Detection
# 🔐 SIEM Brute Force Detection Lab using Splunk

## 📌 Project Overview

This project demonstrates how to detect brute-force login attempts using a SIEM tool. Logs were ingested into Splunk and analyzed to identify suspicious authentication behavior.

---

## 🎯 Objective

To detect multiple failed login attempts from a single IP address within a short time window, indicating a possible brute-force attack.

---

## 🛠️ Tools Used

* Splunk (SIEM platform)
* Sample authentication logs

---

## 📥 Data Source

* Security / authentication logs containing login attempts (successful and failed)

---

## 🔍 Detection Logic

A brute-force attack is identified when:

* Multiple failed login attempts
* From the same IP address
* Within a 5-minute time window

---

## 🧠 SPL Query Used

```
index=your_index failed
| bucket _time span=5m
| stats count by _time, src_ip
| where count > 5
```

---

## 🚨 Alert Configuration

* Trigger Condition: Number of results > 0
* Time Range: Last 5 minutes
* Schedule: Every 5 minutes

---

## 📊 Results

The query successfully identified suspicious IP addresses generating multiple failed login attempts within a short timeframe.

Example finding:

* IP: 73.202.92.7
* Failed Attempts: 99 within 5 minutes

---

## 📸 Screenshots


* Raw logs in Splunk
![alt text](<Screenshot 2026-05-02 145711.png>)
* SPL query execution
![alt text](<Screenshot 2026-05-02 145530.png>)
* Detection results
![alt text](<Screenshot 2026-05-02 145530-1.png>)
* Alert configuration
![alt text](<Screenshot 2026-05-03 150724-3.png>)

---

## 🧠 Skills Demonstrated

* Log ingestion and analysis
* SIEM monitoring
* Detection rule creation
* Basic incident investigation

---

## 🚀 Future Improvements

* Add detection for successful login after multiple failures
* Integrate email alerting
* Expand to multiple log sources

---

## 📬 Author

Sulaimon Aleem

Aspiring SOC Analyst
