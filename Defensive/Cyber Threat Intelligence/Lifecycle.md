![[Pasted image 20260316120004.png]]

**1. Direction – Defining the Mission**
Establish intelligence requirements by identifying critical assets, business risks, and available defensive controls. Translate these into specific, measurable questions that will guide what data needs to be collected and what success looks like.

**2. Collection – Assembling the Raw Material**
Gather raw intelligence from diverse sources such as commercial feeds, open-source databases, internal sharing platforms (e.g., MISP), and vendor reports. Store this data in its original format to ensure reproducibility and provenance.

**3. Processing – Normalising and Correlating the Data**
Standardise the collected data into a consistent format (normalisation) and merge it with existing intelligence to remove duplicates (correlation). Enrich each indicator with metadata such as source, date, and Traffic Light Protocol (TLP) classification. Convert the refined data into machine-readable formats ready for security tools (e.g., firewall blocklists or detection rules).

**4. Analysis – Turning Information Into Judgement**
Assess the relevance and reliability of indicators to the specific environment to minimise false positives. Grade each indicator by confidence (e.g., High, Medium, Low) based on factors like source agreement and local sightings. Determine appropriate actions—such as immediate blocking, alerting, or monitoring—based on this grading.

**5. Dissemination – Getting Intelligence to the Right Consumers**
Distribute tailored intelligence to relevant stakeholders in formats suited to their needs. Technical teams receive machine-readable rules and lists, while management receives strategic summaries. Ensure that the sensitivity and detail level match the audience and honour TLP restrictions.

**6. Feedback – Measuring and Refining the Cycle**
Evaluate the effectiveness of the intelligence through metrics such as dwell time reduction and false-positive rates. Use these findings to validate whether the initial requirements were met, and update the direction phase for the next iteration to continuously improve the program.