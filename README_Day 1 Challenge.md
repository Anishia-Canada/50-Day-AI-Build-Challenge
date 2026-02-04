# Federated Asset Inventory Platform
## Day 1 | 50-Day AI Challenge | SSC (Shared Services Canada)

![Version](https://img.shields.io/badge/version-1.0.0-blue)
![Status](https://img.shields.io/badge/status-complete-green)
![AI Powered](https://img.shields.io/badge/AI-powered-cyan)

---

## 🎯 Overview

The **Federated Asset Inventory Platform** is an AI-powered web application that transforms semi-structured asset data into classified, risk-assessed, and zone-recommended inventory entries. Built for government security operations, it enables administrators to paste raw asset information and receive instant AI analysis with executive dashboard visualization.

### The Problem
- Manual asset classification takes 15-30 minutes per asset
- Inconsistent risk assessments across analysts
- No standardized approach to network zone recommendations
- Difficult to maintain audit trails for security decisions

### The Solution
- **AI-powered classification** in milliseconds
- **Consistent risk scoring** using documented formulas
- **Policy-compliant zone recommendations** based on ITSG-22/38
- **Built-in audit trail** with reasoning for every decision

---

## ✨ Features

### Admin Console
- 📝 Paste semi-structured asset data (flexible format)
- 🤖 AI-powered analysis with 4-layer detection
- 📊 Real-time risk calculation with formula transparency
- 🏷️ Automatic flag detection (20 exception types)
- 🔍 Expandable details for each asset

### Executive Dashboard
- 📈 Risk distribution visualization
- 🍩 Department breakdown charts
- ⚠️ Issues requiring attention summary
- 📋 Department comparison table
- 🕐 Timestamp tracking for audit

### AI Capabilities
| Function | Description |
|----------|-------------|
| **Classify** | 9 asset types via 4-layer detection hierarchy |
| **Detect** | Data category (Confidential/Private/Sensitive/Public) |
| **Calculate** | Risk score (0-100%) with 5 contextual factors |
| **Recommend** | Network zone (PAZ/OZ/REZ/HSZ/MZ or DEV/TEST/STAGING/LAB) |
| **Validate** | 20 exception types with graceful degradation |

---

## 🚀 Quick Start

### Option 1: Direct Browser
1. Download `day1-federated-asset-platform-FINAL.html`
2. Open in any modern browser (Chrome, Firefox, Edge, Safari)
3. No server or installation required!

### Option 2: Local Server
```bash
# Clone the repository
git clone https://github.com/your-org/federated-asset-inventory.git

# Navigate to directory
cd federated-asset-inventory

# Serve with Python
python -m http.server 8000

# Open browser to http://localhost:8000
```

---

## 📖 Usage Guide

### Step 1: Paste Asset Data
Enter assets in the Admin Console using this format:
```
ASSET-NAME, DEPARTMENT
Description of the asset with relevant details

ASSET-NAME-2, DEPARTMENT
Another asset description
```

### Step 2: Analyze
Click **"Analyze Assets"** to process. AI will:
- Parse and validate input
- Classify asset type
- Assess data criticality
- Calculate risk score
- Recommend network zone
- Detect problems/flags

### Step 3: Review Results
- Expand each asset to see detailed reasoning
- Review flags and warnings
- Verify AI recommendations

### Step 4: View Dashboard
Click **"View Executive Dashboard →"** for:
- Aggregate metrics
- Risk distribution charts
- Department breakdown
- Issues summary

---

## 📊 Sample Data

```
CRA-WEB-PORTAL-01, CRA
Public citizen portal for tax filing, internet exposed, production, handles taxpayer PII and payment processing

SSC-SRV-EMAIL-01, SSC
Internal email server for departmental communications, production environment, protected B employee data

PSPC-APP-REPORT-01, PSPC
Internal reporting application for procurement analytics, business operational data, internal network only

SSC-SRV-DEV-01, SSC
Development server for testing new features, isolated network, sandbox environment, test data only, non-production
```

**Expected Results:**
| Asset | Risk Level | Zone |
|-------|------------|------|
| CRA-WEB-PORTAL-01 | Critical | REZ |
| SSC-SRV-EMAIL-01 | Critical/High | REZ |
| PSPC-APP-REPORT-01 | Medium | OZ |
| SSC-SRV-DEV-01 | Low | DEV |

---

## 🧮 Risk Calculation Model

### Formula
```
Risk % = Base Score + Environment + Exposure + Function + Data Residency + AI Confidence
```

### Base Score (Data Category)
| Category | Criticality | Base |
|----------|-------------|------|
| Confidential | Critical | 100% |
| Private | High | 75% |
| Sensitive | Medium | 50% |
| Public | Low | 25% |
| Unknown | Medium | 50% |

### Context Adjustments
| Factor | Range |
|--------|-------|
| Environment | -25% to +15% |
| Exposure | -15% to +20% |
| Function | -10% to +15% |
| Data Residency | -10% to +10% |
| AI Confidence | 0% to +15% |

### Risk Thresholds
| Score | Level |
|-------|-------|
| 0-25% | Low |
| 26-50% | Medium |
| 51-75% | High |
| 76-100% | Critical |

---

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    USER INTERFACE                           │
│  ┌─────────────────────┐  ┌─────────────────────────────┐  │
│  │   Admin Console     │  │   Executive Dashboard       │  │
│  │   - Input textarea  │  │   - Metrics cards           │  │
│  │   - Asset list      │  │   - Charts (Chart.js)       │  │
│  │   - Detail panels   │  │   - Department table        │  │
│  └─────────────────────┘  └─────────────────────────────┘  │
└─────────────────────────────┬───────────────────────────────┘
                              │
┌─────────────────────────────▼───────────────────────────────┐
│                    AI ANALYSIS ENGINE                        │
│  ┌──────────┐ ┌──────────┐ ┌──────────┐ ┌──────────┐       │
│  │ Parser   │→│ Classifier│→│ Risk Calc│→│ Zone Rec │       │
│  │          │ │          │ │          │ │          │       │
│  │ Step 1   │ │ Step 2   │ │ Step 3   │ │ Step 4   │       │
│  └──────────┘ └──────────┘ └──────────┘ └──────────┘       │
│                                                             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              CONFIGURATION (CONFIG object)            │  │
│  │  - Department aliases    - Asset type keywords        │  │
│  │  - Risk adjustments      - Problem detection          │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

---

## 📁 Project Files

| File | Description |
|------|-------------|
| `day1-federated-asset-platform-FINAL.html` | Main application (single-file SPA) |
| `day1-ai-value-proposition.md` | AI justification and value metrics |
| `finalized-risk-calculation-summary.md` | Risk calculation documentation v2.0 |
| `day1-exception-handling-registry.md` | 20 exceptions (EXC-001 to EXC-020) |
| `day1-synthetic-asset-dataset.md` | 250 test assets for validation |
| `day1-dashboard-design.md` | Dashboard UI specification |
| `day1-security-by-design.md` | Security considerations |
| `day1-isaca-ai-audit.md` | ISACA AI auditing report |

---

## 🔐 Security Considerations

- **No external data transmission** - All processing happens client-side
- **No persistent storage** - Data cleared on browser refresh
- **No authentication bypass** - Role badges are visual only (demo)
- **Input validation** - All inputs parsed and sanitized
- **Graceful degradation** - Errors flagged, not hidden

---

## 🏛️ Government Context

### Departments Supported
- CRA (Canada Revenue Agency)
- DND (Department of National Defence)
- SSC (Shared Services Canada)
- PSPC (Public Services and Procurement Canada)
- Service Ontario
- City of Halifax

### Standards Referenced
- **ITSG-22** - Baseline Security Requirements for Network Security Zones
- **ITSG-38** - Network Security Zoning
- **TBS Directive on Security Management** - Data categorization
- **SIA (Security Impact Assessment)** - Risk methodology

---

## 📈 Performance Metrics

| Metric | Manual | AI-Powered | Improvement |
|--------|--------|------------|-------------|
| Time per asset | 15-30 min | <1 sec | 99.9% faster |
| 250 assets batch | 2-3 weeks | <5 sec | Weeks → Seconds |
| Consistency | Variable | 100% | Eliminates variance |
| Audit trail | Manual docs | Automatic | Built-in compliance |

---

## 🛠️ Technical Details

### Technologies Used
- **HTML5** - Structure
- **CSS3** - Styling (CSS Variables, Flexbox, Grid)
- **JavaScript (ES6+)** - Logic (no frameworks)
- **Chart.js** - Dashboard visualizations

### Browser Compatibility
- Chrome 80+
- Firefox 75+
- Edge 80+
- Safari 13+

### No Dependencies Required
- Single HTML file
- CDN-loaded Chart.js (optional, for charts)
- No build process
- No server required

---

## 🗺️ Roadmap

### Future Enhancements
- [ ] Export to CSV/PDF
- [ ] Asset filtering and search
- [ ] Batch import from Excel
- [ ] API integration for automated feeds
- [ ] Role-based access control
- [ ] Persistent storage option
- [ ] Multi-language support

---

## 📜 License

This project is part of the **50-Day AI Challenge** for government security operations. Internal use only.

---

## 👥 Contributors

| Role | Responsibility |
|------|----------------|
| Security Architect | Requirements, SIA methodology |
| AI Engineer | Classification logic, risk model |
| UI/UX Designer | Dashboard design, accessibility |
| QA Analyst | Test data, validation |

---

## 📞 Support

For questions or issues:
1. Review the exception handling registry
2. Check the risk calculation summary
3. Contact the project team

---

## 🏆 50-Day AI Challenge

**Day 1 of 50** | Project 1 of 50

This project demonstrates AI-powered automation for government security operations, delivering:
- ✅ Time savings (99.9% reduction)
- ✅ Business process automation
- ✅ Workflow automation
- ✅ Productivity improvement
- ✅ Resource optimization

---
Day 1_ Video Intro -https://youtu.be/xZ4ycDAfszE 

Day 1_ Code Build-https://youtu.be/nbpX1kPi41A

Day 1_Final Cut-https://youtu.be/RZ4NxzhWFZI
