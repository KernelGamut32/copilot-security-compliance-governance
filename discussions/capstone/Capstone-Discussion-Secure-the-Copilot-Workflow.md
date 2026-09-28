# Integrated Capstone Discussion: Secure the Copilot Workflow

## Incident Review Board - Federal Publications Modernization Program

**Course:** Copilot Under Control: Security, Compliance, Governance, and Responsible Data Use
**Covers:** Slides 31 - 35 (Integrated Capstone)
**Duration:** 30 minutes
**Format:** Facilitated group discussion with evidence review, layer deliberations, and a live rebuild of the Copilot Control Matrix
**Environment:** U.S. Government Publishing Office - Microsoft 365 GCC tenant

---

## Your Role

You are not the participants in this incident. You are the **Incident Review Board** convened after it.

A colleague caught an internal planning detail in an executive briefing draft moments before it would have gone to an external audience. Leadership does not want a scapegoat. Leadership wants to know **which control, at which layer, should have prevented this - and what changes so it does not happen again.**

By the end of this discussion, your board will produce a completed **Copilot Control Matrix** and a defensible answer to the question that opened this course:

> "Copilot found it. Is that a security incident?"

---

## How the 30 Minutes Run

| Time | Part | Slide | What the board does |
|---|---|---|---|
| 0:00 - 0:03 | 1. Convene the Board | 31 | Take your layer assignment and the standard of proof |
| 0:03 - 0:10 | 2. Establish the Facts | 32 | Read the evidence packet and separate what it proves from what it does not |
| 0:10 - 0:18 | 3. Layer Deliberations | 33 | Each team answers its diagnostic questions and one trap question |
| 0:18 - 0:25 | 4. Build the Control Matrix | 34 | Report findings, fill the matrix live, test it with "change one variable" |
| 0:25 - 0:30 | 5. Return to the Opening Poll | 35 | Re-vote, defend your reasoning, and take the Monday question home |

---

## Ground Rules for the Board

1. **"Copilot did it" is not a finding.** Copilot retrieved content the user was authorized to access. If that is where your analysis stops, you have not started.
2. **Every finding points to evidence.** Cite a card in the evidence packet or a documented Microsoft 365 behavior. No speculation about what Copilot "probably" did.
3. **Match the control to the problem.** A sensitivity label does not fix a permission problem. RCD does not fix a missing label. Say which problem you are solving before you name a control.
4. **Absence is evidence.** What does NOT appear in the audit record matters as much as what does.
5. **Authorized is not the same as appropriate.** The user could read everything Copilot used. That is the beginning of the question, not the end of it.

---

## Part 1 - Convene the Board (Slide 31) - 3 minutes

The capstone slide names four layers. Each team owns one:

| Team | Layer | Owns these matrix rows | Owns these diagnostic questions |
|---|---|---|---|
| Team 1 | **Security** | Identity, Access | Q1, Q3 |
| Team 2 | **Compliance** | Protection, Prevention, Monitoring, Investigation | Q7, Q8, Q9 |
| Team 3 | **Governance** | Governance, Remediation (technical) | Q4, Q5, Q6 |
| Team 4 | **Responsible Use** | User behavior, Remediation (behavioral) | Q2, Q10, Q11 |

If the room is smaller than four teams, combine Security with Governance and Compliance with Responsible Use. If the room is larger, run two boards in parallel and compare matrices at the end.

**Standard of proof:** Your board's findings will be read by a program director who was not in this room. Every recommendation must say **what is wrong, which control fixes it, who owns the fix, and how you would confirm the fix worked.**

---

## Part 2 - Establish the Facts (Slide 32) - 7 minutes

### Scenario Recap

A GPO program office is preparing an external publication. A program analyst used Microsoft 365 Copilot Chat to assemble an executive briefing intended for public release. The draft contained an internal planning detail. A colleague in Public Affairs recognized the detail from an internal meeting and stopped the release.

The environment contains eight documents (from slide 32):

| Document | Label | Where it lives | Access condition |
|---|---|---|---|
| Approved_Public_Fact_Sheet.docx | PUBLIC | Public Affairs site | Appropriate access |
| Draft_Publication.docx | INTERNAL | FPMP Program Office site | Broad site access |
| Program_Status_Report.docx | INTERNAL | FPMP Program Office site | Overly broad SharePoint access |
| Historical_Project_Summary.docx | None | Historical Projects site | Stale content, ownerless site |
| External_Research.pdf | None (external source) | Program analyst's OneDrive | Uploaded from outside the organization |
| Acquisition_Planning_Notes.docx | CONFIDENTIAL | Acquisition Planning site | Restricted group |
| Personnel_Assignments.xlsx | CONFIDENTIAL | HR Operations site | Excessive membership |
| Leadership_Briefing.docx | RESTRICTED | Executive Planning site | Leadership group only |

### The Evidence Packet

Your facilitator will walk through the five cards in order. Read each one and answer: **What does this prove? What does it NOT prove?**

---

#### Evidence Card A - Incident Timeline

All times are Eastern. The user is **Jordan Reyes, Program Analyst, Federal Publications Modernization Program** (a synthetic persona).

| When | Event |
|---|---|
| Thu Sep 24, 10:07 AM | Jordan submits a prompt in Microsoft 365 Copilot Chat (work grounding) from the Microsoft 365 Copilot app |
| Thu Sep 24, 10:09 AM | Jordan pastes the response into a new Word document, makes light edits, and saves it as FPMP_Executive_Briefing_DRAFT.docx on the FPMP Program Office site |
| Thu Sep 24, 3:40 PM | Jordan emails the draft to Public Affairs for release review |
| Fri Sep 25, 8:15 AM | The Public Affairs reviewer flags one sentence about print procurement consolidation. She recognizes it from an internal planning meeting she attended |
| Fri Sep 25, 9:30 AM | Release halted. Program office requests an incident review |

---

#### Evidence Card B - The Prompt

The prompt below was obtained by an authorized investigator through a Microsoft Purview eDiscovery search of Jordan's Copilot interactions. Jordan confirmed it in interview.

> "Draft a two-page executive briefing on the Federal Publications Modernization Program for external release. Use everything we have on program status, milestones, timeline, and what comes next. Make it sound confident and complete."

Note what the prompt asks for and what it never says: no named sources, no exclusions, no request for citations, no instruction to separate public-safe facts from internal planning, and no mention that anything in the environment might not be releasable.

---

#### Evidence Card C - The CopilotInteraction Audit Record

Retrieved from Microsoft Purview Audit by filtering on the **CopilotInteraction** operation for Jordan's account on September 24. Shown here in readable form; the portal displays it as JSON in the AuditData field. Identifiers are synthetic.

```
RecordType:      261 (CopilotInteraction)
Operation:       CopilotInteraction
Workload:        Copilot
UserId:          jordan.reyes@fpmpdemo.onmicrosoft.com
CreationTime:    2026-09-24T14:07:12Z
ClientRegion:    US
AppIdentity:     Copilot.MicrosoftCopilot.BizChat

CopilotEventData:
  AppHost:        BizChat
  AISystemPlugin: []
  Contexts:       []
  ThreadId:       19:9c41d0f7e2ab4b0e8b6d5a3f1c2e7d90@thread.v2

  Messages:
    - Id: 1758722832041   isPrompt: true    JailbreakDetected: false
    - Id: 1758722838907   isPrompt: false

  AccessedResources:
    - Name:               Approved_Public_Fact_Sheet.docx
      Type:               docx
      Action:             Read
      Status:             Success
      SensitivityLabelId: 9a1d0f6e-2b3c-4d5e-8f70-1a2b3c4d5e01
      SiteUrl:            https://fpmpdemo.sharepoint.com/sites/PublicAffairs/Shared Documents/Approved_Public_Fact_Sheet.docx
      XPIADetected:       false

    - Name:               Program_Status_Report.docx
      Type:               docx
      Action:             Read
      Status:             Success
      SensitivityLabelId: 3f2c8b1a-7e6d-4c5b-9a80-2b3c4d5e6f02
      SiteUrl:            https://fpmpdemo.sharepoint.com/sites/ProgramOffice/Shared Documents/Program_Status_Report.docx
      XPIADetected:       false

    - Name:               Draft_Publication.docx
      Type:               docx
      Action:             Read
      Status:             Success
      SensitivityLabelId: 3f2c8b1a-7e6d-4c5b-9a80-2b3c4d5e6f02
      SiteUrl:            https://fpmpdemo.sharepoint.com/sites/ProgramOffice/Shared Documents/Draft_Publication.docx
      XPIADetected:       false

    - Name:               Historical_Project_Summary.docx
      Type:               docx
      Action:             Read
      Status:             Success
      SensitivityLabelId: (none)
      SiteUrl:            https://fpmpdemo.sharepoint.com/sites/HistoricalProjects/Shared Documents/Historical_Project_Summary.docx
      XPIADetected:       false

  ModelTransparencyDetails:
    ModelProviderName: OpenAI
```

**Label ID lookup** (resolved in the Purview portal; the audit record stores only the GUID):

| SensitivityLabelId | Label name |
|---|---|
| 9a1d0f6e-2b3c-4d5e-8f70-1a2b3c4d5e01 | PUBLIC |
| 3f2c8b1a-7e6d-4c5b-9a80-2b3c4d5e6f02 | INTERNAL |

Things to notice before your facilitator points them out:

- Four resources were read. Eight exist in the environment.
- AISystemPlugin is empty. No web grounding occurred.
- JailbreakDetected is false on the prompt. XPIADetected is false on every resource.
- One accessed resource carries no SensitivityLabelId at all.
- The record tells you **which** files were used. It does not contain the prompt or response text. That came from eDiscovery (Card B).

---

#### Evidence Card D - SharePoint Data Access Governance Excerpt

Compiled from the SharePoint admin center Data Access Governance reports and site properties for the six sites in scope. Simplified for discussion.

| Site | Owner | Members group contains | Sharing links in use | Last content activity | Site label | Restricted Content Discovery |
|---|---|---|---|---|---|---|
| Public Affairs | 2 named owners | Public Affairs team (14) | None | 3 days ago | Public | Off |
| FPMP Program Office | 1 named owner | **Everyone except external users** | 2 "People in your organization" links | 1 day ago | None | Off |
| Historical Projects | **No owner** | Legacy security group "FPMP Program Alumni" (63) | 1 "People in your organization" link | **14 months ago** | None | Off |
| Acquisition Planning | 1 named owner | Acquisition Team (6) | None | 2 days ago | Confidential | Off |
| HR Operations | 1 named owner | HR Operations plus 3 departmental groups (212) | None | Today | Confidential | Off |
| Executive Planning | 1 named owner | FPMP Leadership (9) | None | Today | Restricted | Off |

Jordan is a member of the FPMP Program Alumni group from a prior detail assignment in 2024. Nobody has reviewed that group's membership since the site lost its owner.

---

#### Evidence Card E - Source Comparison

Two passages in the draft briefing were traced back to their sources.

**Passage 1 - the sentence that stopped the release**

| In the draft briefing (intended for external release) | In Program_Status_Report.docx, Section 6, headed "Internal planning considerations - not for external release" |
|---|---|
| "The program anticipates consolidating its two regional print procurement contracts into a single vehicle in FY27, subject to appropriations." | "Pending appropriations, the program office anticipates consolidating the two regional print procurement contracts into a single vehicle in FY27. Not for external release until the acquisition strategy is approved." |

**Passage 2 - the sentence nobody flagged**

| In the draft briefing | In Historical_Project_Summary.docx (last modified 14 months ago) | In Approved_Public_Fact_Sheet.docx (current) |
|---|---|---|
| "Public launch of the modernized publication portal is planned for Q2 FY26." | "Public launch of the modernized publication portal is planned for Q2 FY26." | "Public launch of the modernized publication portal is planned for Q1 FY27." |

Passage 2 was not caught by anyone. It would have published a superseded date as current fact.

---

### Discussion Questions for Part 2

Work through these as a full board before splitting into teams.

1. **What does the audit record prove?** Be precise: which user, which app, which resources, which labels, and what did not happen.
2. **Which four documents were NOT accessed, and why does their absence matter?** What does that tell you about whether the authorization model worked?
3. **Two governance failures produced two different defects.** One source was over-permissioned. The other was unlabeled, stale, and ownerless. Are these the same problem? Would the same control fix both?
4. **The prompt said "use everything we have."** Copilot did exactly that. At what moment in the timeline did this incident become inevitable?
5. **A human caught Passage 1 because she happened to attend a meeting.** Is that a control? What catches the next one when nobody in the review chain has that knowledge?

---

## Part 3 - Layer Deliberations (Slide 33) - 8 minutes

Split into teams. Each team answers its diagnostic questions from the eleven on slide 33, then answers one **trap question** designed to expose the most common misconception about that layer.

Each team prepares a report of **no more than 90 seconds** containing:

- Three findings, each tied to a card in the evidence packet
- One primary control and one supporting control, with the problem each one solves
- One owning role (not a person) for the remediation
- One validation method that proves the fix worked

---

### Team 1 - Security (Identity and Access)

**Q1. What happened?** Trace the content from source to output using Cards C and E.

**Q3. Was the user actually authorized?** Check the permission chain for every resource in AccessedResources using Card D. Then list the four resources that were NOT accessed and explain, for each, why the authorization model kept them out.

**Trap question:** If GPO removes Jordan's Copilot license tomorrow, is the underlying risk gone?

---

### Team 2 - Compliance (Protection, Prevention, Monitoring, Investigation)

**Q7. Should a sensitivity label apply?** Which content is mislabeled, under-labeled, or unlabeled? What label and what protection setting would you recommend for each, and what would that change about Copilot's behavior?

**Q8. Is DLP appropriate?** Design a DLP policy for the Microsoft 365 Copilot and Copilot Chat location that would have helped here. State which condition and which action. Then state what it would NOT have caught.

**Q9. What audit evidence should be reviewed?** List every evidence source available to an investigator, what each one contains, and what permissions or licensing it depends on.

**Trap question:** Would a DLP rule for the Copilot location have stopped Historical_Project_Summary.docx from being used? Why or why not?

---

### Team 3 - Governance (Governance and Technical Remediation)

**Q4. Was the information overshared?** Which site condition on Card D enabled each of the two defects on Card E? Name the oversharing pattern from slide 21 for each.

**Q5. Should permissions change?** For each of the two sites involved, say exactly what changes permanently: which group is removed, which group replaces it, who owns the site, and what happens to the site if no owner can be found.

**Q6. Would RCD be appropriate temporarily?** For which sites, for how long, and what has to be true before you remove it? What does RCD not do for you?

**Trap question:** Your team applies Restricted Content Discovery to the FPMP Program Office site. Jordan opens Program_Status_Report.docx in Word and asks Copilot to summarize it. Does RCD stop that?

---

### Team 4 - Responsible Use (User Behavior and Behavioral Remediation)

**Q2. Security, compliance, governance, or user behavior?** Assign a percentage of responsibility to each layer and defend it with evidence. Your total must equal 100.

**Q10. What should the user have done differently?** Rewrite Jordan's prompt as a governed request using the pattern from slide 30. Then list what Jordan should have done with the response before it left the program office.

**Q11. How should the organization prevent recurrence?** Name one policy change, one training change, and one technical change. For each, say what problem it solves that the other two do not.

**Trap question:** Jordan says: "I was authorized to read every document Copilot used. Nothing I did was against policy." Is Jordan wrong?

---

## Part 4 - Build the Control Matrix (Slide 34) - 7 minutes

Teams report in order: Security, Compliance, Governance, Responsible Use. As each team reports, the facilitator fills the matrix on the board. Challenge any decision that does not name the problem it solves.

### The Copilot Control Matrix

| Layer | Question | Board decision |
|---|---|---|
| Identity | Who is the user? What Entra identity and role? | |
| Access | What can they access? What M365 permissions apply? | |
| Governance | Should they have that access? Is it appropriate? | |
| Protection | How sensitive is the information? What labels apply? | |
| Prevention | Should Copilot process it? Is DLP appropriate? | |
| Monitoring | How do we detect usage? What audit records exist? | |
| Investigation | What evidence exists? What do CopilotInteraction records show? | |
| User behavior | Was the use appropriate? Was the prompt well-constructed? | |
| Remediation | What should change? Permissions, labels, DLP, training, or all? | |

### Stress Test - Change One Variable

Once the matrix is filled, the board tests it. For each counterfactual, decide in under a minute: **Does the incident still happen? What changed, and what did not?**

**Counterfactual 1 - Encryption.** Program_Status_Report.docx had been labeled CONFIDENTIAL with encryption, and Jordan's group held VIEW but not EXTRACT.

**Counterfactual 2 - DLP.** A DLP policy for the Microsoft 365 Copilot and Copilot Chat location excluded INTERNAL-labeled files from processing.

**Counterfactual 3 - RCD.** Restricted Content Discovery had been applied to both the FPMP Program Office site and the Historical Projects site the week before.

**Counterfactual 4 - The prompt.** Jordan had written: "Using only Approved_Public_Fact_Sheet.docx, draft a two-page executive briefing for external release. Cite the source for every claim. Do not use any other document. Flag anything you cannot support from that file."

After all four: **Which single change was cheapest? Which was most durable? Which one would you not want to rely on alone? Why is the answer to those three questions not the same control?**

---

## Part 5 - Return to the Opening Poll (Slide 35) - 5 minutes

### Re-vote

The same seven options from the opening slide. Vote again.

- Copilot
- The user
- SharePoint permissions
- The data owner
- The governance process
- Security
- Everyone to some degree

If your vote changed, be ready to say in one sentence what evidence changed it.

### The Four Questions on Slide 35

Answer each in one sentence, citing the matrix:

1. Was it Copilot's fault?
2. Was it the user's fault?
3. Was it the governance process?
4. What fixes it?

### The Monday Question

Take this one home. Write your answer on the exit card before you leave:

> "The first thing I would check in my own environment on Monday is ________, because the evidence in this case showed ________."

---

## Appendix A - The Eleven Diagnostic Questions by Layer

| # | Question | Layer | Team |
|---|---|---|---|
| 1 | What happened? Trace the content from source to output | Security | 1 |
| 2 | Security, compliance, governance, or user behavior? Or a combination? | Responsible Use | 4 |
| 3 | Was the user actually authorized? Check the permission chain | Security | 1 |
| 4 | Was the information overshared? Which site condition enabled this? | Governance | 3 |
| 5 | Should permissions change? Permanent remediation vs. temporary control | Governance | 3 |
| 6 | Would RCD be appropriate temporarily? While permissions are reviewed? | Governance | 3 |
| 7 | Should a sensitivity label apply? Which content needs classification? | Compliance | 2 |
| 8 | Is DLP appropriate? Should Copilot be restricted from processing this content type? | Compliance | 2 |
| 9 | What audit evidence should be reviewed? CopilotInteraction records, resources referenced, labels captured | Compliance | 2 |
| 10 | What should the user have done differently? Prompt construction, grounding constraints, verification | Responsible Use | 4 |
| 11 | How should the organization prevent recurrence? Policy, training, and technical controls | Responsible Use | 4 |

---

## Appendix B - Team Worksheet

**Team:** ____________________ **Layer:** ____________________

| Finding | Evidence card | Problem it reveals |
|---|---|---|
| 1. | | |
| 2. | | |
| 3. | | |

| Control | Primary or supporting | Problem it solves | What it does NOT solve |
|---|---|---|---|
| | | | |
| | | | |

**Owning role:** ____________________

**Validation method:** ____________________

**Trap question answer (one sentence):** ____________________

---

## Appendix C - Reference Behaviors You May Cite

These are documented Microsoft 365 behaviors that may be cited as evidence in your findings. Your facilitator has the Microsoft Learn sources.

- Copilot operates in the security context of the signed-in user and returns only content that user is already authorized to access.
- When a sensitivity label applies encryption, Copilot returns data from an item only if the user holds the EXTRACT usage right in addition to VIEW.
- When Copilot generates new content from labeled sources, the highest-priority label among the sources is used for inheritance where the destination supports it.
- A DLP policy for the Microsoft 365 Copilot and Copilot Chat location can exclude files and emails with chosen sensitivity labels from processing. Excluded items may still appear in citations, but their content is not used. This condition cannot target unlabeled content.
- A DLP policy for the same location can block prompts that contain sensitive information types, and can block web search when prompts contain sensitive information types.
- Restricted Content Discovery limits a site's content in organization-wide search and Microsoft Copilot discovery scenarios. It does not change permissions, does not remove content from the search index, and does not affect experiences operating on content already in use by the user, such as summarizing an open document.
- Restricted SharePoint Search is retiring. New enablement was blocked on July 31, 2026. Full retirement is January 31, 2027.
- Microsoft Purview Audit (Standard) records CopilotInteraction events automatically, including the user, timestamp, AppHost, resources accessed, and sensitivity label IDs on those resources. Prompt and response text is obtained through eDiscovery, not from the audit record.
- Web grounding is off by default in GCC tenants. When it is off, AISystemPlugin in the audit record will not contain BingWebSearch.
