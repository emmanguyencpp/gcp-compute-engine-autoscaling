# Google Cloud Infrastructure: Compute Engine, Custom Image & Auto Scaling

##  Executive Summary
This project demonstrates the implementation of an elastic, highly available infrastructure on Google Cloud Platform (GCP). It covers automated web server deployment via Startup Scripts, Custom Machine Image (IMS) packaging, and Managed Instance Group (MIG) horizontal auto-scaling triggered by simulated CPU load.

##  Technologies & Tools
- **Cloud Provider:** Google Cloud Platform (GCP)
- **Core Services:** Compute Engine (VM), Custom Machine Images, Instance Templates, Managed Instance Groups (MIG), Cloud Shell CLI (`gcloud`)
- **OS & Software:** Debian/Ubuntu, Apache2 Web Server, `stress` tool

##  Key Implementation Steps
1. **Infrastructure Provisioning:** Deployed a baseline Compute Engine VM (`e2-medium`) with an automated Bash startup script to install Apache2 and test web server connectivity.
2. **Custom Image Packaging:** Terminated baseline instance to create a standardized, reusable Custom Machine Image (`my-custom-web-image`) for rapid horizontal cloning.
3. **Template & Group Setup:** Configured an Instance Template and instantiated a Managed Instance Group (MIG) with an initial replica count of 1.
4. **Auto Scaling Policy:** Configured a metric-based scaling policy targeting 50% CPU utilization with a 60s cooldown period (Min: 1 VM, Max: 4 VMs).
5. **Load Testing & Verification:** Performed synthetic CPU load generation using `stress` via SSH. Successfully validated horizontal auto-scaling from **1 VM to 4 VMs** dynamically.

##  Empirical Test Metrics
| Metric | Extracted Parameter / Value |
| :--- | :--- |
| **Custom Image Family** | `my-web-family` |
| **Scaling Target** | 50% CPU Utilization (`0.50`) |
| **Pre-load Capacity** | 1 Replica (`my-auto-mig`) |
| **Post-load Capacity** | **4 Replicas** (Scale Out Triggered) |

---
*Author: Nguyễn Thị Thùy Hương | Specialist: Computer Networking & Data Communications*
