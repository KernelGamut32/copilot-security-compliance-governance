# The Briefing Is Ready. Can We Defend It?
## A 30-minute Microsoft Purview decision room

**Participant discussion**  
**Course:** Copilot Under Control - Security, Compliance, Governance, and Responsible Data Use  
**Coverage:** Slides 12-19, Module 2: Compliance  
**Format:** Groups of 3-5, followed by short leadership briefings  
**Companion file:** `Copilot_Slides_12-19_Facilitator_Guide.md`

> **Your mission:** Keep an important publication moving, prevent inappropriate use of sensitive information, and explain what the evidence actually proves. A list of product names is not a decision.

## Before you begin

This is an invented case in the deck's **Federal Publications Modernization Program** setting. It does not describe an actual GPO incident, configuration, records schedule, or policy. All people, documents, labels, timestamps, and evidence are synthetic. PUBLIC, INTERNAL, and CONFIDENTIAL are exercise sensitivity-label names, not national-security classification markings.

Use the case facts and slides. Your facilitator will identify any current Microsoft documentation qualifications separately. No tenant sign-in, administrative rights, real sensitive information, meeting recording, or transcription is required. Proposed technology must be verified for the actual GCC tenant before operational use.

**Read each evidence card only when directed.** The exhibits are normalized teaching summaries, not literal Purview exports. Times such as 09:12 belong to the fictional incident; times such as 03:00 below are elapsed classroom time.

### Bring four perspectives

| Perspective | Your contribution |
| --- | --- |
| Program lead | Protect the publication deadline without treating urgency as permission to release. |
| Information-protection lead | Identify the exact item, rights, policy location, and behavior that need attention. |
| Records and investigation lead | Request proportionate evidence and confirm what is actually preserved. |
| Evidence challenger | Ask what is known, what is inferred, and what would change the team's conclusion. |

Combine perspectives in smaller groups. Choose a recorder and spokesperson. Everyone contributes before anyone speaks twice.

### The 30-minute schedule

| Elapsed time | Decision | Required output |
| --- | --- | --- |
| 00:00-03:00 | The deadline and the assurance | Initial decision and one evidence request |
| 03:00-09:00 | Round 1: Where should protection apply? | Source-to-draft risk explanation |
| 09:00-16:00 | Round 2: Design a control that solves the right problem | Two complementary actions and a validation test |
| 16:00-24:00 | Round 3: Build a defensible evidence chain | Supported finding, preservation scope, and unresolved question |
| 24:00-28:00 | Leadership briefings and challenge | A 60-second recommendation |
| 28:00-30:00 | Reconsider and transfer | One practical lesson for your work |

---

## Opening | 00:00-03:00
### The deadline and the assurance

At 09:20, Morgan, a publications coordinator, has a draft update ready for external release at 10:00. Morgan used Microsoft 365 Copilot Chat and copied its response into a new Word document.

A colleague notices this sentence:

> "The program has a 17-day contingency window for the supplier transition."

The program owner confirms that this planning detail is **not approved for external release**. No external distribution has yet been established. A screenshot of the Copilot response includes a link to an encrypted acquisition document.

A manager says:

> "The acquisition document is encrypted, the staging site is labeled CONFIDENTIAL, and we have DLP. There are no alerts. The audit log should prove that everything worked. Can we send it?"

**Vote individually:** Release the current draft, pause this draft while continuing safe work, or suspend all Copilot work pending investigation?

**Discuss:** Which part of the manager's assurance most needs evidence? Ask for one specific artifact, not simply "more information."

**Initial decision and first evidence request:** __________________________

---

## Round 1 | 03:00-09:00
### Where should protection apply?

**Slide connection:** The control stack, classification, encryption, usage rights, and inheritance on slides 13-14.[^deck13][^deck14]

### Evidence Card A - Source inventory at 09:12

For this case, Morgan is an intended reader of all four sources. Do not solve the exercise by assuming Morgan's membership is wrong. The exercise label priority is **PUBLIC < INTERNAL < CONFIDENTIAL**.

| ID and source | Actual file label and protection | Relevant case fact |
| --- | --- | --- |
| **F1** `Approved_Public_Fact_Sheet.docx` | PUBLIC; no label encryption | Current, approved facts are sufficient for a shorter external update. |
| **F2** `Draft_Publication.docx` | INTERNAL; no label encryption | Contains working dates that have not been approved for release. |
| **F3** `Acquisition_Planning_Notes.docx` | CONFIDENTIAL; label-applied encryption; Morgan has VIEW but not EXTRACT | Contains the 17-day detail. Morgan is not the encryption owner. Other authorized reviewers have VIEW and EXTRACT. |
| **F4** `Production_Staging_Notes.docx` | No file label; no encryption | Stored on a site labeled CONFIDENTIAL. The owner considers its contents internal working material. Its relevant historical text has not yet been examined. |

**F5** `External_Update_Draft.docx` is the new Word document. It was created by ordinary copy-and-paste from chat, not a demonstrated label-inheritance workflow. Its actual file label and protection have not been checked.

### Make two decisions

**1. Explain the protection boundary.** Morgan can open F3 directly. Should that settle whether Copilot may summarize it? Does a source link prove its protected text was used? Then explain what you would inspect on F4 rather than relying on its site's label.

**2. Protect the new artifact.** Compare a supported Copilot creation workflow with Morgan's copy-and-paste route. What must be verified on F5 itself? Who decides the appropriate handling and release status when the output combines sources or contains sensitive information from an unlabeled file?

**Your challenge:** Would assigning F5 a PUBLIC label make the unapproved sentence appropriate to release? Explain your reasoning without merely saying "follow policy."

**Record one sentence:** "The boundary we must verify is __________ because __________."

---

## Round 2 | 09:00-16:00
### Design a control that solves the right problem

**Slide connection:** DLP location, blocking, restriction, and layered controls on slides 15 and 19. This expands the control-selection challenge on slides 17-18.[^deck15][^deck17][^deck19]

### Evidence Card B - What "we have DLP" means here

The administrator confirms that the existing policy covers **outbound Exchange email containing specified bank-account identifiers**. It is not a policy targeting the Microsoft 365 Copilot and Copilot Chat location. The disputed sentence contains no bank-account identifier.

A proposed Copilot rule would exclude files carrying the CONFIDENTIAL label. It is **not deployed**. Its entitlement, GCC availability, user scope, enforcement state, and observed behavior have not been verified. Nobody has established an automatic release-approval mechanism for F5.

Three colleagues propose shortcuts:

> "Just label the site again."
>
> "Remove EXTRACT from every document for every employee."
>
> "Tell Copilot to use only public information. That should be our control."

### Your design task

Choose **two complementary actions**, not two names for the same action. At least one must address the source or processing boundary; the other must address the draft's handling or release. State what can continue today using F1.

For each action, identify **the actual item or workflow, the accountable role, and the remaining risk**. Reject one shortcut and explain its operational cost or coverage gap.

For your proposed technical control, specify one **must-block test** and one **must-allow test**. A screen showing "policy created" is not your acceptance test. State the fallback while the feature or configuration remains unverified.

| Action | Exact scope and owner | Remaining risk or verification |
| --- | --- | --- |
| Source or processing boundary | | |
| Draft handling or release | | |

**Must block:** ____________________ **Must allow:** ____________________

### Boundary stress test - Your facilitator assigns one row

These are separate design variations, not additional facts about Morgan's original interaction. Do not enter real identifiers into any tool.

| Variation | Requirement to defend |
| --- | --- |
| **A - Typed prompt** | A user types sensitive identifiers into a prompt. The organization wants that prompt not to be processed. |
| **B - Web grounding** | An approved internal inquiry may proceed, but sensitive prompt context must not drive external web search. |
| **C - Incoming email** | Staff may read vendor email, but the organization wants external-sender email excluded from Copilot reasoning. |

In one sentence, distinguish **what your control should stop, what should remain usable, and what it does not control**. Does your answer govern incoming grounding content, the typed request, external web search, or outbound distribution?

---

## Round 3 | 16:00-24:00
### Build a defensible evidence chain

**Slide connection:** CopilotInteraction, retention, eDiscovery, and the six-part summary on slides 16-19.[^deck16][^deck19]

### Evidence Card C - Authorized investigation findings

The records and investigation team provides these synthetic findings. Do not infer additional fields, events, or searches.

| Exhibit | What was actually obtained |
| --- | --- |
| **C1 - Activity metadata** | A `CopilotInteraction` event for Morgan at 09:12; application host `BizChat`; resource references F1, F2, and F4; message references P-042 and R-043. The prompt's `JailbreakDetected` value is false. This digest supplies no web-participation or DLP-evaluation result. |
| **C2 - Interaction content** | Authorized eDiscovery review retrieves the prompt and response corresponding to P-042 and R-043. The response contains the 17-day sentence and cites F4 beside it. It separately links to F3 and indicates that F3 could not be summarized. |
| **C3 - Historical source** | F4 version 2, the version available at 09:12, contains the 17-day sentence. Its owner had copied this planning text into F4 for internal coordination. Version 3, edited at 09:25, removes the sentence. Both versions are currently available. |
| **C4 - Saved output** | F5 version 1 contains the same sentence. Inspection shows no applied file sensitivity label. It is still in a review library. Morgan recalls seeing an INTERNAL sensitivity indicator in the chat. |
| **C5 - Limited distribution check** | A search of Morgan's sent items for 09:00-09:20 finds no matching external email. Later activity, other senders, sharing links, and other distribution paths have not been examined. |
| **C6 - Preservation status** | Relevant material is currently retrievable. A preservation request has been submitted, but no one has confirmed its effective scope. Copilot interaction retention, source/draft retention, and audit-log retention have not been reconciled. |

### Answer three questions

**1. What happened, and how certain are we?** Connect C1, C2, C3, and C4. Explain what the audit event establishes and what required content review. Does this evidence support the theory that Copilot bypassed F3's protection? What does `JailbreakDetected = false` fail to establish?

**2. What must survive the investigation?** Identify a proportionate evidence set covering **activity metadata, interaction content, source/draft versions, and distribution evidence**. Assign an accountable role. Explain why a hold request for one location would not, by itself, prove that this entire evidence set is preserved.

**3. What may leadership be told?** State one supported finding and one unresolved issue. Does C5 justify saying "nothing was disclosed externally"? What additional check would most improve that conclusion?

### At the facilitator's signal: The director's request

> "Delete the conversation and replace the staging note so we remove the risk. If that is not possible, retain everything across the tenant forever. I need a decision now."

Give a response that distinguishes **containing exposure, preserving evidence, and applying approved retention requirements**. Do not invent a GPO retention period or assume that a request has already become an effective hold.

---

## Leadership briefing | 24:00-28:00

Complete the brief below in short phrases. Your facilitator will hear two contrasting recommendations. Every other team listens for one unsupported assurance and one strong decision.

| Briefing line | Your recommendation |
| --- | --- |
| **Now:** What pauses, and what safe work continues? | |
| **Prevent:** Which source/processing action and release action will you take? | |
| **Verify:** What result must a control test demonstrate, and who owns it? | |
| **Preserve:** Which evidence categories and versions need confirmed coverage? | |
| **Explain:** What is established, what remains unknown, and what happens next? | |

**The challenge from the room:** "Which part of your recommendation would fail if your most important assumption were wrong?"

Do not answer with "enable Purview" or "apply all controls." Explain a decision, its scope, its evidence, and its tradeoff.

---

## Closing | 28:00-30:00

Revisit your opening vote. Did new evidence change your diagnosis, your release decision, or both?

Complete this sentence individually:

> "Even when __________ works correctly, we still need __________ because __________."

Name one real workflow where you would now check the **source, the generated artifact, and the evidence trail separately**. Describe the workflow generically; do not disclose real sensitive details.

## Source basis

The control vocabulary and sequence come from the attached deck. The scenario, evidence, role perspectives, tradeoffs, and decision template are instructional additions. The facilitator guide supplies separately labeled Microsoft Learn qualifications checked on September 28, 2026; the exercise does not assert commercial/GCC feature parity.

[^deck13]: Attached deck, *Copilot Under Control: Security, Compliance, Governance, and Responsible Data Use*, slide 13, "2.1 The Compliance Control Stack." Slide 12 introduces Module 2.
[^deck14]: Same deck, slide 14, "2.2 Sensitivity Labels and Copilot."
[^deck15]: Same deck, slide 15, "2.3 DLP and Copilot."
[^deck16]: Same deck, slide 16, "2.4 Audit - Following the Evidence."
[^deck17]: Same deck, slides 17-18, "2.5 Compliance Mini-Challenge," question and answer versions.
[^deck19]: Same deck, slide 19, "Module 2 - Compliance Summary."
