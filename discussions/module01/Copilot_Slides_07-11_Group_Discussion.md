# Same Permissions. New Visibility.
## Group discussion: Copilot found it in 20 seconds. What actually changed?

**Participant discussion sheet**  
**Course:** Copilot Under Control - Security, Compliance, Governance, and Responsible Data Use  
**Coverage:** Slides 7-11, Module 1: Security Fundamentals  
**Duration:** 18 minutes; your facilitator may use a 15- or 20-minute version  
**Format:** Groups of 3-5, followed by brief whole-class responses

> **Your mission:** Explain the evidence, challenge an overconfident assurance, and recommend a response that protects information without unnecessarily stopping legitimate work.

This fictional exercise uses the deck's GPO/GCC setting and Federal Publications Modernization Program. Morgan, the documents, group names, and evidence are invented for discussion; they do not describe an actual GPO incident or policy. Use only this case and slides 7-11. No live Copilot session, administrative access, or real organizational information is needed.

## How we will work

Choose a spokesperson who also records brief notes. Bring three perspectives into the conversation: the **program lead** wants work to continue, the **data owner** questions who should see the information, and the **evidence checker** asks what the facts actually establish. Everyone should contribute before your group reports back.

Read each round only when the facilitator calls it. Keep answers to a sentence or a few notes; this is a discussion, not a documentation exercise.

| Elapsed time | Discussion | Team output |
| --- | --- | --- |
| 00:00-02:00 | The surprising answer | Initial hypothesis and an evidence request |
| 02:00-06:00 | Round 1: Did Copilot cross a boundary? | An evidence-based diagnosis |
| 06:00-10:00 | Round 2: Protected does not settle every question | A corrected assurance and a grounding distinction |
| 10:00-15:00 | Round 3: Fix the problem without stopping the mission | A prioritized response with accountable roles |
| 15:00-18:00 | Myth/reality vote and closing reflection | One practical takeaway |

## Opening: The surprising answer

Morgan, a publications coordinator, signs in with a work account and asks Microsoft 365 Copilot:

> "Summarize this week's production-readiness risks for our internal coordination meeting."

Within 20 seconds, Copilot produces a response that includes an unannounced staffing proposal and cites an internal planning document. Morgan says, "I didn't know that document existed."

A colleague responds:

> "That proves Copilot can search the whole tenant. We should switch it off."

**Vote individually:** Is the strongest initial explanation **a permission bypass**, **pre-existing access that may be too broad**, or **not enough evidence yet**? A plausible hypothesis is not the same as a verified diagnosis.

**Discuss briefly:** What single piece of evidence would you request first, and why?

**Our first evidence request:** ________________________________________

## Round 1: Did Copilot cross a boundary?

**Slide connection:** The security mental model and authorization chain on slide 8.[^s8]

### Evidence Card A - Read when directed

For this case, the following checks establish access **at the time of the interaction, for Morgan's signed-in identity**. The original response used organizational work grounding; it did not use web search. No agents, additional connectors, or alternative copies of these documents are part of the case.

| Document | Morgan's direct access | Permission and intended audience | Observed response |
| --- | --- | --- | --- |
| `Weekly_Production_Risks.docx` | Can open | Morgan belongs to the program team and is an intended reader. | Cited in the response. |
| `Staffing_Options_Working_Draft.docx` | Can open | An existing `Program-All-Staff` group grants read access. The owner intended access only for six planning leads; Morgan is not one of them. | Cited; the staffing proposal matches this source. |
| `Director_Decision_Record.docx` | Cannot open | Access is limited to a directors' group; Morgan is not a member. | Not a source for the response. |

The broad group permission existed before Copilot was introduced. These are document names, not sensitivity-label designations.

### Discuss

**Trace the chain.** Using slide 8, explain the roles of **Entra Authenticate -> M365 Authorize -> Graph Retrieve -> Copilot Orchestrate** in this case. Where is the file-access decision made?

**Make the diagnosis.** Does the evidence support a Copilot permission bypass, an inappropriate existing permission, or neither? Explain the difference between **Morgan can access it** and **Morgan should have access**. Use the directors' document as a comparison, without claiming that one example proves every control is perfect.

**Our diagnosis, supported by one case fact:** __________________________

Be ready to explain your conclusion in 20 seconds.

## Round 2: Protected does not settle every question

**Slide connection:** Enterprise Data Protection (EDP), work grounding, and web grounding on slide 9.[^s9]

A manager says:

> "Our Copilot data is encrypted, isolated from other tenants, and not used to train Microsoft's foundation models. Therefore, this staffing result cannot represent an information-access problem."

### Decision A - Challenge the conclusion, not every reassurance

Which protections in that statement are supported by slide 9? What conclusion does **not** follow from them? Explain what the organization still needs to decide or manage, including access and its existing policies.

**Our two-sentence response to the manager:** __________________________

### Evidence Card B - A separate follow-up request

This is a new request, not an explanation for the original staffing result. For a later comparison of **publicly available publishing practices**, an administrator has enabled web search in this fictional GCC environment.

A teammate says:

> "GCC defaults to web search off, so no query can leave for Bing. Besides, work grounding and web queries have exactly the same DPA coverage."

**Decision B:** Use the distinction on slide 9 to correct that statement. How does a **default setting** differ from the **setting actually enabled**? What does the slide say is sent to Bing, what is not sent, and how are the governing commitments different?

**Our corrected boundary statement:** _________________________________

Do not invent a web query containing staffing details or use real sensitive information.

## Round 3: Fix the problem without stopping the mission

**Slide connection:** Zero Trust, the seven protection layers, and the discoverability shift on slide 10.[^s10]

Consider the slide's question:

> "What changes when an employee can discover in 20 seconds what used to take them 45 minutes to locate?"

The program lead needs the weekly production work to continue. The site owner says, "That broad permission has been there for two years, and nobody complained." A colleague proposes disabling Copilot instead of reviewing the permission.

### Make a practical recommendation

First, agree on **what changed and what did not**. Identify one legitimate productivity benefit and one risk of easier discovery.

Next, complete the three short rows below. Mark the **first priority** with an asterisk and name an accountable role. Use slide 10's seven-layer list to identify the layer most directly affected by that first action; you do not need to design seven separate controls.

| Zero Trust principle | One concrete action or evidence check | Responsible role |
| --- | --- | --- |
| Verify Explicitly |  |  |
| Use Least Privilege |  |  |
| Assume Breach |  |  |

**Layer addressed by our first priority:** _____________________________

**Our 30-second recommendation:** "First, ___, owned by ___. We will verify ___ and review ___. We will preserve legitimate work by ___. Disabling Copilot alone would/would not resolve the access issue because ___."

Use ordinary role names rather than guessing GPO's actual ownership structure. You are recommending a response, not making a final incident classification.

### Two-minute extension - Only when the facilitator calls it

Change one fact: the data owner now confirms that Morgan **is** an intended reader, and the existing group contains exactly the approved audience.

What part of your original diagnosis would change? What would still need verification? Can surprise alone establish that access was inappropriate?

## Close: Myth or reality?

**Slide connection:** The four knowledge-check statements on slide 11.[^s11]

Vote **M** for myth or **R** for reality. Be ready to support your choice with the case, not just a memorized answer. The facilitator will reveal or revisit slide 11 after voting.

| Statement | M or R? | Case evidence or reason |
| --- | --- | --- |
| "Copilot can search every file in the tenant." |  |  |
| "Copilot creates a new Microsoft 365 permission system." |  |  |
| "Existing oversharing becomes more important with Copilot." |  |  |
| "Good identity and permission hygiene is part of Copilot security." |  |  |

**Individual closing reflection - 30 seconds:** Complete these two sentences.

> "The most important distinction in this case is ___."
>
> "Before treating a surprising Copilot answer as proof of a security failure or proof that everything is fine, I would verify ___ because ___."

## Source and scope

Slide numbers are the PDF's one-based page numbers, including the title slide. The activity follows slide 7's Module 1 structure: security model, EDP, Zero Trust, and myth/reality review.[^s7] The GPO/GCC setting and fictional program name come from the deck's opening framing on slides 1 and 3. All scenario details and discussion tasks are teaching additions.

The technical reference for this exercise is the supplied deck, not an independent assessment of current feature availability, tenant configuration, or GPO incident-handling requirements. Detailed compliance controls and later course modules are outside this discussion.

[^s7]: *Copilot Under Control: Security, Compliance, Governance, and Responsible Data Use*, supplied PDF, slide 7, "Security Fundamentals: What Copilot Can Actually Access."
[^s8]: Same deck, slide 8, "1.1 The Copilot Security Mental Model"; see the four-stage authorization-chain diagram and its key principle.
[^s9]: Same deck, slide 9, "1.2 Enterprise Data Protection (EDP)"; see the five commitments and the separate Work Grounding and Web Grounding sections.
[^s10]: Same deck, slide 10, "1.3 Zero Trust Meets Copilot"; see the three principles, seven protection layers, and discoverability question.
[^s11]: Same deck, slide 11, "1.4 Security Knowledge Check - Myth or Reality?"
