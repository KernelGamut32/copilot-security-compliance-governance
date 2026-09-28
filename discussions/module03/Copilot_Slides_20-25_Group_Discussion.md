# The Oversharing Hunt: Six Sites, Two Changes
## Participant guide | Copilot Under Control, slides 20-25

**Duration:** 18 minutes, with instructor-led 15- or 20-minute variants  
**Team:** 3-4 participants  
**Required evidence:** `Copilot_Slides_20-25_SAM_Data_Access_Governance_Report.docx`  
**Scenario:** Federal Publications Modernization Program, fictional GPO/GCC environment

> The review board has capacity for two coordinated access-remediation work packages today. Which two changes would you authorize, what legitimate work would you protect, and what evidence would convince you that the changes worked?

All case records are synthetic. Do not use actual agency data, sign in to a tenant, or change any permissions during this discussion.

## Your mission

Review six SharePoint sites before an expansion of Copilot-assisted briefing preparation. Some signals represent a genuine mismatch between access and business need. Others are appropriate collaboration, incomplete evidence, or a separate governance problem.

Find **at least three evidence-supported concerns**, choose **two access-remediation priorities**, and identify **one apparently concerning signal that does not justify restricting access on the evidence provided**. You are not expected to exhaust every possible issue in the packet.

A strong finding answers this question:

> **Which content can which people access, through which permission path, and why does that conflict with the approved business audience?**

Naming a sensitive site, a large number, or a control is not enough. Cite the record IDs that establish the mismatch. Also distinguish an access risk from evidence that the information was actually used in a Copilot answer or sent outside the organization.

## Assign roles, then investigate

Choose an **evidence reader** to trace access paths, a **business advocate** to protect necessary collaboration, and a **verifier/spokesperson** to challenge assumptions and report the decision. With four participants, split the evidence-reader role between permissions/membership and content/lifecycle. All roles contribute to the final recommendation.

Do not read the eight-page report cover to cover. Its page numbers and record IDs are your navigation system.

| Report page | What it provides | Use it to answer |
|---|---|---|
| 2 | SAM-style snapshot and recent-sharing activity | Where should we investigate first? What does this number actually measure? |
| 3 | Approved business audiences and site configuration, B01-B06 | Who should have access, and to which content? |
| 4 | Selected permission paths, P01-P07 | Which grant reaches the file or folder? Does inheritance widen or narrow access? |
| 5 | Group membership and link context, G01-G04 and L01-L04 | Who is really in the audience? What does the link permit, and was it redeemed? |
| 6 | Sample content and lifecycle records, D01-D06, O01-O02, H01 | Is the content current, protected, owned, and subject to preservation? |
| 7 | Control checks and access tests, C01-C03 and T01-T03 | What changed? What behavior was actually tested? |

Pages 1 and 8 provide provenance, dates, reporting limits, and references. They are reference pages rather than required reading during the timed review.

## The 18-minute discussion

### 0:00-2:00 | Accept the assignment

Read the mission and assign roles. Your two changes must be specific, coordinated work packages, not "fix everything" or "turn off Copilot."

For each priority, you must preserve the named, approved audience. Other concerns cannot disappear from the plan: name an accountable owner and a next step for anything you defer. Escalate urgent exposure rather than using the two-change constraint as permission to leave it unmanaged.

### 2:00-5:00 | Compare the signals with the business purpose

Scan report pages 2-3 together. Nominate three sites for deeper review, but do not finalize their risk from the dashboard alone.

Discuss:

- Which signal most strongly deserves investigation? What other evidence is needed before calling it oversharing?
- Could the busiest site be appropriately shared? Could a quiet site still permit inappropriate access?
- Are you comparing current permissions, recent sharing events, or an approved business roster? Those are different measures.

### 5:00-10:00 | Build the permission story

Divide the targeted reading. One reader follows pages 4-5; another checks pages 6-7. Bring the evidence back to the group.

Use the following sentence for each concern:

> "Record ___ establishes the approved audience. Record ___ shows the access path to ___. Record ___ explains why the actual or potential audience is wider, or why further verification is needed."

Pressure-test your conclusions:

**Scope:** Are you describing the entire site, one library, one folder, or a single item?  
**Identity:** Does the visible team roster include every separately assigned security group?  
**Time:** Could the permission predate the activity window? Is a control check newer than the snapshot?  
**Certainty:** Is this confirmed inappropriate access, an unresolved governance concern, or an unsupported suspicion?

Complete the evidence board below. Short phrases and record IDs are enough.

| Site and content | Evidence IDs and access mismatch | Finding status | Primary response |
|---|---|---|---|
| 1. | | | |
| 2. | | | |
| 3. | | | |

**A signal we would not treat as oversharing without more evidence:**  
`Site / record IDs / reason: __________________________________________`

### 10:00-12:00 | Challenge a reassuring statement

Read **RQ01, C01, and T01 on report page 7**:

> "The discovery restriction is enabled. Please confirm whether we can close the access-review ticket."

Decide whether the ticket should close. Explain which requirement the control addresses, which requirement remains, and what an acceptable closure test would look like.

Then challenge one other reassurance from the report. Possibilities include a Private site, a reviewed team roster, no new sharing activity, a site sensitivity label, or a requirement to retain content. Choose one and explain exactly what it does and does not establish.

### 12:00-15:00 | Authorize two precise changes

Use the four-problem framework on slide 22. Select the response that addresses the actual problem, then add supporting controls only where they serve a stated purpose.

| Problem to solve | Control family from the slides |
|---|---|
| A user should not have access | Permissions remediation / Restricted Access Control |
| Broad discovery should be temporarily limited during review | Restricted Content Discovery |
| The information requires protection | Sensitivity labels / DLP |
| Evidence must be monitored, preserved, or investigated | Audit / retention / eDiscovery |

Complete two short decision cards. Aim for no more than 70 words per card.

**Decision 1**  
`Site and exact scope:`  
`Evidence IDs and reason for priority:`  
`Access change; people who must retain access:`  
`Business owner + technical owner:`  
`Outside-audience test + approved-user test:`

**Decision 2**  
`Site and exact scope:`  
`Evidence IDs and reason for priority:`  
`Access change; people who must retain access:`  
`Business owner + technical owner:`  
`Outside-audience test + approved-user test:`

**One deferred concern:** `Owner / interim handling / next review date or deadline.`  
**One fact still unknown:** `What additional evidence would resolve it?`

Treat any proposed GCC feature as subject to tenant verification. A sound decision names the intended behavior and a permission-remediation alternative, not just a product switch.

### 15:00-18:00 | Defend the decision

Prepare a **45-second report-out**. The facilitator will select a few teams; all teams retain their evidence boards.

> "Our first change is ___ because records ___ show ___. Our second is ___. We will preserve access for ___. We are not restricting ___ merely because ___. We will close the first ticket only when ___. We still need evidence of ___."

When listening to another team, ask one of these questions: **"What is your access path?"**, **"Whose legitimate work might that block?"**, or **"What would prove the fix worked?"**

## Reporting guardrails

**SAM report fields are signals, not a business-approval engine.** The report labels native-report-style values as DAG and supporting fictional records as SUP. The two source families are intentionally separate.

**Do not treat a count as a conclusion.** A zero in the stated activity window does not mean no older permission remains. A user count at any scope does not mean every counted user can open every file. Link creation alone is not proof of organization-wide Copilot discoverability. The report's method notes explain these distinctions using Microsoft Learn references M01-M04.

**Do not invent an incident.** This packet does not contain a Copilot answer, a complete usage history, or evidence of external disclosure. Identify confirmed access mismatches, but state what remains unknown.

**Protect the information and the work.** Your recommendation should remove access that conflicts with the approved purpose while preserving necessary publishing, review, and records work.

## Exit reflection

Complete this sentence before returning to the slides:

> "Before calling a SharePoint site ready for Copilot, I would verify ___ rather than relying only on ___."

### Instructional basis

The supplied *Copilot Under Control: Security, Compliance, Governance, and Responsible Data Use* deck, slides 20-25, supplies the governance framing, oversharing patterns, four-control matching model, RCD distinction, and ownership requirement. The report supplies the fictional case evidence. Current Microsoft Learn qualifications are identified separately in the facilitator guide; they are not additional hidden case facts.
