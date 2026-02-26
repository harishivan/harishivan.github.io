# Real-Time Industrial AI Monitoring Platform

## 1) Problem Definition
Industrial test systems generate very high frequency telemetry data like - speed, torque, vibration, temperature, pressure, voltage, current etc,
Detecting anomalies is usually reactive and manual, even with this large volume of data. <br><br>
Engineers had to - <br>
- define static thresholds.
- perform signal analysis and validation post test.
- manually compare signals based on historical data.
- asses failures after production impact

Core problem :
How can the anomalies be detected in real-time, reduce manual inspection effort and improve the reliability in automation test environments?

## 2) Users & JTBD

**Primary Users**
- Test Engineers
- Validation Engineers
- Production Supervisors

**Secondary Stakeholders**
- Quality Assurance Teams
- Plant Operations
- Engineering Leadership

**Jobs To Be Done**
- Detect deviations early
- Reduce false positives
- Ensure consistent validation across units
- Minimize unplanned downtime

## 3) Oppertunity & Impact
**Baseline challenges:**
- Manual inspection effort
- Delayed anomaly detection
- Inconsistent threshold definitions
- Limited real-time visibility

**Estimated Impact Areas:**
- Undetected anomalies
- Mean Time to Diagnose (MTTD)
- Manual inspection hours
- System reliability
- Standardization across test benches

## 4) North Star Metric
Percentage of Test Runs with Automated Accurate Anomaly Classification.

**Supporting Metrics:**
- False Positive Rate
- False Negative Rate
- Detection Latency
- Engineer Review Time per Test
- System Uptime

## 5) Solution Overview
Designed and implemented a real-time AI-driven monitoring platform.

**High-Level Architecture**

Signal Sources
→ MQTT Streaming Layer
→ FastAPI Ingestion
→ Time-Series Storage (TimescaleDB)
→ ML Anomaly Engine
→ Dashboard & Alerting System

**Key Product Decisions**

1. Real-Time vs Batch Processing
   Chose near-real-time inference for faster operational feedback.

2. Static Thresholds vs Adaptive Models
   Implemented envelope-based dynamic tolerance curves + anomaly detection models.

3. Centralized vs Distributed Monitoring
   Centralized platform for consistent validation across multiple test benches.

## 6) AI & ML Strategy
Implemented: 
- Envelope curve modeling (upper/lower tolerance bands)
- Time-series anomaly detection
- Rolling smoothing techniques
- Multi-channel signal alignment
- Drift monitoring considerations

| Decision Area                       | Trade-Off                                                    |
| ----------------------------------- | ------------------------------------------------------------ |
| Latency vs Accuracy                 | Lower latency required simplified models                     |
| False Positives vs False Negatives  | Tuned toward lower false negatives for safety-critical tests |
| Model Complexity vs Maintainability | Balanced interpretability and performance                    |


## 7) MVP → Iteration Roadmap
**Phase 1 (MVP)**
- Signal ingestion
- Manual envelope comparison
- Basic anomaly flags

**Phase 2**
- Automated envelope generation
- Real-time alert dashboard
- Basic ML classification

**Phase 3**
- Drift monitoring
- Cross-unit anomaly clustering
- Performance analytics dashboard

## 8) Risks & Mitigation

**Risk 1:**High False Positives <br>
**Mitigation:**
- Dynamic threshold tuning
- Engineer-in-the-loop feedback

**Risk 2:**Model Drift Over Time <br>
**Mitigation:**
- Scheduled model revalidation
- Continuous aggregate monitoring

**Risk 3:**Latency Constraints <br>
**Mitigation:**
- Lightweight inference logic
- Efficient streaming architecture

## 9) Business Operational Impact
Observed / Expected Improvements:
- Reduced manual inspection dependency
- Faster anomaly visibility
- Standardized validation logic
- Improved traceability across production runs
- Scalable architecture for future ML expansion

## 10) Key Learnings
- In industrial systems, reliability > model sophistication
- False negatives are often costlier than false positives
- AI systems require monitoring infrastructure as much as modeling
- Clear metrics must be defined before training models
- Engineers trust interpretable models more than black-box outputs

__
