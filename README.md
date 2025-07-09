📌 OVERALL RESEARCH PLAN
✅ We’ll break this into 6 big research modules:
1️⃣ Log Sources
2️⃣ Collection Methods
3️⃣ Parsing & Normalization
4️⃣ Storage Options
5️⃣ Alerting / Correlation
6️⃣ UI / Reporting

✅ For each module:
⭐ What is it?
⭐ Why is it important?
⭐ Real-world examples
⭐ Design considerations
⭐ Our project plan

✅ Module 1: Log Sources
⭐ What is it?
The systems and devices that generate logs we want to monitor.

⭐ Why important?
SIEM’s job is to centralize logs from many sources.

Bad log coverage = missed attacks.

⭐ Examples:
OS logs (Linux auth.log, Windows Event logs)

Web server logs (Apache/Nginx access.log)

Firewall logs

IDS/IPS alerts

Cloud logs (AWS CloudTrail)

Application logs

⭐ Design considerations:
What sources will we support first?

How to handle different log formats?

⭐ OUR PLAN:
✅ MVP focus:
✔️ Local file logs (auth.log, access.log)
✔️ Syslog input (standard for many devices)

✅ Research questions to answer:

What are typical fields in these logs?

How frequently do they update?

✅ Module 2: Collection Methods
⭐ What is it?
How the SIEM gathers logs from the sources.

⭐ Why important?
Without reliable collection → no security visibility.

⭐ Examples:
File tailing (like tail -f)

Syslog server (UDP/514)

Agent-based collection (OSSEC/Wazuh agents)

API collection (CloudTrail APIs)

⭐ Design considerations:
Real-time vs batch

Scalability

Reliability

⭐ OUR PLAN:
✅ MVP focus:
✔️ File tailing (watch and read new lines)
✔️ Basic Syslog UDP listener

✅ Research questions:

How to implement tailing in Python?

How does Syslog protocol work?

✅ Module 3: Parsing & Normalization
⭐ What is it?
Turning raw logs into structured, searchable data.

⭐ Why important?
Raw logs are messy.

Need to extract IPs, users, timestamps, etc.

⭐ Examples:
Regex parsing

JSON logs

Common Event Format (CEF)

Logstash-style pipelines

⭐ Design considerations:
Multiple log formats

Extensible parsing rules

⭐ OUR PLAN:
✅ MVP focus:
✔️ Simple regex-based parsing
✔️ Store raw + parsed fields (JSON)

✅ Research questions:

What fields are critical for detection?

How to make parser rules user-editable?

✅ Module 4: Storage Options
⭐ What is it?
Where processed logs are saved.

⭐ Why important?
Needs to be searchable, scalable.

⭐ Examples:
Relational DBs (SQLite, PostgreSQL)

NoSQL (MongoDB)

Search-focused (Elasticsearch)

⭐ Design considerations:
Query speed

Retention policies

Storage cost

⭐ OUR PLAN:
✅ MVP focus:
✔️ SQLite (simple, embedded)
✔️ Table for logs with raw + parsed data

✅ Research questions:

Best schema for logs?

How to store JSON in SQLite?

✅ Module 5: Alerting / Correlation
⭐ What is it?
Rules that detect suspicious patterns in logs.

⭐ Why important?
SIEM’s value = threat detection.

⭐ Examples:
Keyword matching (e.g. “Failed password”)

Threshold rules (10 logins in 1 min)

Correlation (multiple events over time)

⭐ Design considerations:
User-defined rules

Rule testing/debugging

Alert storage

⭐ OUR PLAN:
✅ MVP focus:
✔️ Simple keyword/regex rules
✔️ CLI alert notification
✔️ Alerts table in DB

✅ Research questions:

How to define rules in config?

How to match logs efficiently?

✅ Module 6: UI / Reporting
⭐ What is it?
How users interact with the SIEM.

⭐ Why important?
No one uses a SIEM with no interface.

⭐ Examples:
CLI searches

Web dashboards

Alert views

⭐ Design considerations:
Ease of use

Security of UI

Query/filter support

⭐ OUR PLAN:
✅ MVP focus:
✔️ CLI commands for:

Log search

View alerts
✔️ Optional Flask-based Web UI later

✅ Research questions:

What CLI experience is intuitive?

How to query SQLite for logs?

✅ Final SIEM Research Checklist
✅ [ ] Study log sources you want to support
✅ [ ] Learn file tailing in Python
✅ [ ] Understand Syslog basics (RFC 5424)
✅ [ ] Research Regex parsing for common logs
✅ [ ] Design SQLite schema for logs + alerts
✅ [ ] Define simple alert rule format (YAML/JSON)
✅ [ ] Plan CLI commands for search/view

