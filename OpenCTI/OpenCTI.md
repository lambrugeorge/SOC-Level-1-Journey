# What I Learned Today: OpenCTI 🚀

Today, I explored the fundamentals of **OpenCTI**, an open-source threat intelligence platform designed to help organizations manage, analyze, and visualize cyber threat data. Here’s a summary of my key takeaways:

## 🌟 What is OpenCTI?

OpenCTI is a collaborative platform developed by the French National Cybersecurity Agency (ANSSI). Its main goal is to provide a comprehensive tool for managing Cyber Threat Intelligence (CTI), allowing users to:

- Store, analyze, and visualize threat campaigns, malware, and IOCs.
- Build relationships between technical and non-technical information.
- Integrate with other tools like **MITRE ATT&CK**, **MISP**, and **TheHive**.

## 🗺️ Navigating the Platform

- The platform uses the **STIX2** standard for structuring data, making it easier to exchange and trace threat intelligence.
- Entities and relationships are central, helping to map out the origins and connections of threat data.

## 🏗️ OpenCTI Architecture

- **GraphQL API**: Connects clients to the database and messaging system.
- **Write Workers**: Handle asynchronous queries via RabbitMQ.
- **Connectors**: Python processes for ingesting, enriching, and exporting data.

### 🔌 Types of Connectors

| Class                        | Description                                   | Examples                        |
|------------------------------|-----------------------------------------------|---------------------------------|
| External Input Connector     | Ingests info from external sources            | CVE, MISP, TheHive, MITRE       |
| Stream Connector             | Consumes platform data stream                 | History, Tanium                 |
| Internal Enrichment Connector| Enriches new entities from user requests      | Observables enrichment          |
| Internal Import File Connector| Extracts info from uploaded reports           | PDFs, STIX2 Import              |
| Internal Export File Connector| Exports info into different file formats      | CSV, STIX2 export, PDF          |

## 🔍 Key Functionalities for Threat Analysis

- Centralized threat data management
- Visualization of relationships between threats
- Integration with other intelligence tools
- Flexible data import/export options

## 📚 My Learning Experience

Understanding OpenCTI helped me see how organizations can better manage and leverage threat intelligence. The platform’s modular architecture and support for industry standards make it a powerful tool for security analysts.

---

> **Tip:** Check out the documentation for more details on configuring connectors and working with the data model!

