# Emery Berger Writing Style Guide

Style guidelines distilled from award-winning papers: Hoard (ASPLOS Most Influential Paper), DieHard (PLDI Most Influential Paper), Reconsidering Custom Memory Allocation (OOPSLA Most Influential Paper), Exterminator (CACM Research Highlight), AutoMan (CACM Research Highlight), BLeak (CACM Research Highlight), PlanAlyzer (CACM Research Highlight), Coz (SOSP Best Paper, CACM Research Highlight), Scalene (OSDI Jay Lepreau Best Paper), ChatDBG (FSE 2025), and Quantifying the Performance of Garbage Collection (OOPSLA 2005).

---

## I. Voice and Tone

### Active Voice, System as Subject
Use active voice with the system or project name as the subject whenever possible. This practice centers the narrative on the artifact rather than the authors, giving the work a life of its own.

- **Do:** "DieHard uses randomization and replication to achieve probabilistic memory safety."
- **Do:** "BLeak leverages the observation that users repeatedly return to the same visual state."
- **Do:** "Coz identifies previously unknown optimization opportunities that are both significant and targeted."
- **Do:** "ChatDBG supports take the wheel debugging via the function call capabilities in OpenAI's API."
- **Do:** "Hoard combines one global heap and per-processor heaps with a novel discipline that provably bounds memory consumption."
- **Do:** "Scalene precisely and simultaneously profiles CPU, memory, and GPU usage, all with low overhead."
- **Acceptable (for human actions):** "Guided by Coz, we improve the performance of Memcached by 9%."
- **Don't:** "We present a system that uses randomization and replication."
- **Don't:** "A runtime system is presented that tolerates these errors."

Use "we" only for actions that genuinely require human agency (designing experiments, making implementation choices, writing patches). For everything the system does, the system should be the grammatical subject.

Reserve passive voice for cases where the agent is genuinely unknown or unimportant, or to vary sentence rhythm occasionally.

### No Contractions
Never use contractions in formal paper writing. Write "do not," "cannot," "does not," "it is," etc.

### Confident, Direct Assertions
Make claims directly and back them immediately with evidence. Do not hedge unnecessarily.

- **Do:** "Surprisingly, for six of these applications, a state-of-the-art general-purpose allocator performs as well as or better than the custom allocators."
- **Do:** "Exterminator automatically corrects heap-based memory errors without programmer intervention."
- **Don't:** "It seems that the general-purpose allocator might perform comparably in some cases."

### More Hemingway, Less Faulkner
Prefer short, declarative sentences. Each sentence should convey one idea clearly. Avoid nested clauses, excessive qualification, and long-winded constructions.

- **Do:** "These errors can lead to program crashes, security vulnerabilities, and unpredictable behavior." (one clear list)
- **Do:** "Causal profiling works by running performance experiments during program execution." (direct statement of mechanism)
- **Don't:** "These errors, which can, in various circumstances and depending on the nature of the underlying memory corruption that has occurred, potentially lead to a variety of undesirable outcomes including but not limited to crashes..."

When a sentence exceeds roughly 25-30 words, consider splitting it.

---

## II. Abstract Structure

The abstract follows a strict four-part formula in a single dense paragraph:

1. **Problem** (1-2 sentences): State the problem and why it matters. Ground it in real-world impact.
2. **Gap/Limitation** (1 sentence): What is wrong with current approaches.
3. **Approach** (2-3 sentences): What the paper contributes. Name the system/technique. Make the system the subject.
4. **Results** (1-2 sentences): Concrete, quantitative outcomes.

### Example pattern (from Coz):
> "Improving performance is a central concern for software developers. [PROBLEM] To locate optimization opportunities, developers rely on software profilers. However, these profilers only report where programs spent their time: optimizing that code may have no impact on performance. [GAP] This paper introduces causal profiling. ... Coz identifies previously unknown optimization opportunities that are both significant and targeted. [APPROACH, SYSTEM AS SUBJECT] Guided by Coz, we improve the performance of Memcached by 9%, SQLite by 25%, and accelerate six PARSEC applications by as much as 68%. [RESULTS]"

Always include specific numbers in the abstract. Percentages, counts, and concrete measurements make the abstract compelling.

---

## III. Introduction Structure

The introduction is the most critical section. It follows a consistent narrative arc across all papers:

### 1. Open with the Broad Problem (1 paragraph)
Start with a statement that any computer scientist can understand. Establish why the area matters. When applicable, use external rankings, surveys, or adoption numbers to establish the significance of the domain.

> "Parallel, multithreaded C and C++ programs such as web servers, database managers, news servers, and scientific applications are becoming increasingly prevalent."

> "Improving performance is a central concern for software developers."

> "Python is now firmly established as one of the most popular programming languages, with first place rankings from TIOBE and IEEE Spectrum, second place on the RedMonk Rankings, and fourth place in the 2022 Stack Overflow Developer Survey. Large-scale industrial users of Python include Dropbox, Facebook, Instagram, Netflix, Spotify, and YouTube."

Multiple independent sources of evidence (rankings, surveys, named companies) are more persuasive than a single claim.

### 2. Narrow to the Specific Problem (1-2 paragraphs)
Identify the specific pain point. Use concrete examples.

> "Unfortunately, the memory allocator is often a bottleneck that severely limits program scalability on multiprocessor systems."

> "Tracking down their location in the source code is difficult, and even for critical security-sensitive bugs, the average time between initial reports and the issuance of a patch is nearly 1 month."

### 3. Explain Why Existing Approaches Fail (1-2 paragraphs)
Systematically enumerate the shortcomings of prior work. Be specific about what each class of approach gets wrong.

> "Previous allocators suffer from problems that include poor performance and scalability..."

> "Because previous leak detection approaches designed for conventional C, C++ or Java applications are ineffective in the browser environment, tracking down leaks currently requires intensive manual effort."

### 4. Introduce Your Solution (1-2 paragraphs)
Name the system. State the key insight or mechanism. Make the system the subject of most sentences.

> "This paper introduces causal profiling. Unlike past profiling approaches, causal profiling indicates exactly where programmers should focus their optimization efforts, and quantifies their potential impact."

> "DieHard tolerates these errors while probabilistically maintaining soundness. DieHard uses randomization and replication to achieve probabilistic memory safety."

### 5. Summarize Key Results (1 paragraph)
Give the headline numbers. Make the reader want to keep reading.

> "Guided by Coz, we improve the performance of Memcached by 9%, SQLite by 25%, and accelerate six PARSEC applications by as much as 68%; in most cases, these optimizations involve modifying under 10 lines of code."

### 6. List Contributions Explicitly
Use a numbered or bulleted list. Each contribution should reference the section where it is developed.

> "This paper makes the following contributions:
> 1. It presents causal profiling, which identifies code where optimizations will have the largest impact (&sect;2).
> 2. It presents Coz, a causal profiler that works on unmodified Linux binaries (&sect;3)."

---

## IV. Sentence-Level Style

### System as Subject
Default to the system name as the grammatical subject. This convention produces more vivid, concrete prose and avoids the vague "we."

- **Do:** "BLeak then automatically generates a list of leaks found along with their root causes, ranked by return on investment."
- **Do:** "Exterminator exploits randomization to pinpoint errors with high precision."
- **Do:** "Hoard improves on previous memory allocators by simultaneously providing four features."
- **Do:** "PlanAlyzer checks PlanOut programs for a variety of threats to internal validity."
- **Do:** "Scalene's CPU profiler turns these limitations of Python signals to its advantage, inferring whether a line spent its time executing Python or native code."
- **Do:** "Scalene uses Laplace's Rule of Succession to compute the likelihood of a success or failure in the next Bernoulli trial."
- **Don't:** "We then automatically generate a list of leaks."
- **Don't:** "We exploit randomization to pinpoint errors."

Use "we" for design decisions, experimental methodology, and human judgment calls:
- "We evaluate Coz on a range of highly-tuned applications."
- "We chose to place a progress point immediately after the barrier."
- "Guided by BLeak, we identify and fix over 50 memory leaks."

### Lead with the Point
Put the conclusion or key claim at the beginning of the sentence or paragraph, not buried at the end.

- **Do:** "Surprisingly, for six of these applications, a state-of-the-art general-purpose allocator performs as well as or better than the custom allocators."
- **Don't:** "After examining eight applications, we found that, for six of them, something surprising occurred: the general-purpose allocator was comparable."

### Use Concrete Examples
Whenever possible, ground abstract claims with specific, real-world instances.

- "...web servers, database managers, news servers, and scientific applications..."
- "...Memcached by 9%, SQLite by 25%..."
- "...popular libraries and apps including Airbnb, AngularJS, Google Analytics, Google Maps SDK, and jQuery."

### Quantify Everything
Replace vague qualifiers with numbers.

- **Do:** "...the average time between initial reports and the issuance of a patch is nearly 1 month."
- **Do:** "...these optimizations involve modifying under 10 lines of code."
- **Don't:** "...it takes a long time to fix these bugs."
- **Don't:** "...these optimizations are small."

### Strategic Use of "Surprisingly"
Use "surprisingly" (or similar) when presenting results that defy conventional wisdom. This word signals to the reader that they should pay attention.

> "Surprisingly, for six of these applications, a state-of-the-art general-purpose allocator performs as well as or better than the custom allocators."

Do not overuse it. Reserve it for genuinely counterintuitive findings.

### Parallel Structure
When listing items, use consistent grammatical forms.

- **Do:** "...speed, scalability, false sharing avoidance, and low fragmentation." (all nouns/noun phrases)
- **Do:** "...including failing to dispose of unneeded event listeners, repeatedly injecting iframes and CSS files, and failing to call cleanup routines." (all gerund phrases)

---

## V. Paper Organization

### Standard Structure
The papers consistently follow this section ordering:

1. **Abstract**
2. **Introduction** (with explicit contributions list)
3. **Background / Motivating Example** (optional, but common)
4. **Design / Approach / Overview**
5. **Implementation**
6. **Evaluation / Experimental Results**
7. **Related Work** (placed late, before conclusion)
8. **Conclusion**

### Related Work Placement
Related work appears near the end of the paper, not in the introduction. This placement is deliberate: the reader first understands the paper's contribution, then can appreciate how it differs from prior work. The introduction may briefly note that prior approaches are insufficient, but the detailed comparison belongs in a dedicated late section.

### Motivating Example
Several papers (BLeak, PlanAlyzer, Coz) open with a concrete motivating example immediately after the introduction. This example:
- Is small enough to understand quickly
- Illustrates the core problem vividly
- Shows why existing tools fail on this specific case
- Demonstrates the paper's solution on the same example

> "Figure 1 shows a simple program that illustrates the shortcomings of existing profilers." (Coz)

> "This memory leak is in Firefox's debugger, which is a pure HTML5 application." (BLeak)

### Extended Interactive Examples
For interactive or agentic systems, include multi-step session transcripts as figures. These walkthroughs serve as both motivation and demonstration, showing the system's behavior in action rather than just describing it.

> ChatDBG's Figure 2 shows a complete debugging session: the user asks "why?", ChatDBG examines stack frames, autonomously issues debugger commands (taking the wheel), and converges on the root cause with a fix—all in a single extended figure.

These extended examples should:
- Be drawn from realistic (ideally real) scenarios
- Show the system making autonomous decisions, not just responding to commands
- Include enough context (source code, error messages) to be self-contained
- Be referenced repeatedly from the technical sections that explain each step

### Historical Context Tables
When situating a new tool within a long lineage, a historical feature-comparison table can be powerful. Map features across decades to show how the field has evolved and where your contribution fits.

> ChatDBG's Table 1 compares debugger features from 1961 (DEC Debugging Tape) through 2023, showing that ChatDBG is the first to combine LLM-driven exploration with traditional debugging capabilities.

---

## VI. Evaluation Style

### Pose Explicit Evaluation Questions
Open the evaluation section with a list of specific questions the evaluation will answer.

> "Our evaluation addresses the following questions:
> - Precision: How precise is BLeak's memory leak detection?
> - Accuracy of diagnoses: Does BLeak accurately locate the code responsible for memory leaks?
> - Overhead: Does BLeak impose acceptable overhead?"

> "Our evaluation answers the following questions: (1) Does causal profiling enable effective performance tuning? (2) Are Coz's performance predictions accurate? (3) Is Coz's overhead low enough to be practical?"

### Use Real-World Benchmarks
Always evaluate on real, widely-known applications, not just synthetic benchmarks.

- Hoard: larson, cache-scratch, cache-thrash, real web server workloads
- DieHard: Squid, Mozilla
- Coz: Memcached, SQLite, PARSEC
- BLeak: Airbnb, Gmail, Firefox Debugger, Google Maps SDK
- Scalene: pyperformance suite, plus external case studies (Rich, Pandas, Semantic Scholar)

### Present Results with Precision
Include error bars, confidence intervals, or statistical tests.

> "...9.39% +/- 0.95% speedup."
> "All speedups are statistically significant at the 99.9% confidence level."
> "BLeak's median precision is 100%."

### Comparison Tables and Figures
Use summary tables that let the reader quickly grasp the main results. Figures should have detailed captions that can be understood without reading the body text.

Consider placing a comprehensive feature-comparison table early (even in the introduction or as Figure 1), showing your system vs. all competitors across every relevant dimension. Scalene's Figure 1 is an exemplar: a single table comparing 15 profilers across 13 feature dimensions, making the breadth of Scalene's contribution immediately visible.

### Sub-Section Summaries
Within evaluation sections, use bold **Summary:** callouts to provide a one- or two-sentence takeaway at the end of each subsection. These orient skimming readers and reinforce findings.

> "**Summary:** Scalene's memory profiling is highly accurate, while capturing memory consumption over time."

> "**Summary:** Among the accurate memory profilers, Scalene operates with the lowest overhead (median: 1.32x vs. 3.98x (memray) and 2.71x (Fil)), while capturing memory usage over time and producing small log files."

### Ablation Studies via Progressive Feature Enablement
When the system has multiple components, demonstrate the contribution of each through progressive enablement. This approach shows that every feature earns its place.

> ChatDBG evaluates five configurations—Default Stack, Enriched Stack, +Take the Wheel, +Targeted Question, and +Dialog—each adding one feature to the previous configuration. This progression shows that enriched stacks help with crashes, "take the wheel" is critical for semantic errors, and multi-step dialog raises the overall success rate from 57% to 85%.

Structure the ablation so each step is a clean addition. Present results for all configurations side by side in a single figure or table.

### Boxed RQ Summaries
End each research question's analysis with a visually distinct, boxed summary that directly answers the question posed. These are more specific than sub-section summaries: they restate the RQ and give the headline answer.

> **RQ1 Summary:** Even with just the simple question *why?*, ChatDBG was successful 57% of the time. With questions specialized to the target's particular error, that number jumps to 67%, and with an additional dialog step ChatDBG succeeded in identifying and fixing the defect in 85% of the trials.

> **RQ2 Summary:** While all features of ChatDBG contribute to its success, the technical innovations enabling it to take the wheel are critical.

### Report Cost and Resource Consumption
When a tool consumes external resources (API calls, compute time, money), report the actual cost transparently. This transparency builds trust and helps practitioners judge feasibility.

> "...a cost of about $0.12 USD under OpenAI's current pricing model." (ChatDBG, Python)

> "Average time (27 seconds) and cost ($0.06 USD) were comparable to Python." (ChatDBG, C/C++)

Include cost alongside effectiveness metrics so readers can evaluate the cost-benefit tradeoff.

### Benchmark Provenance and Justification
Explicitly justify why your benchmarks are appropriate. Note when benchmarks are unpublished (avoiding data leakage), when bugs are from real humans (not synthetically generated), and when they cover diverse error categories.

> "Unlike many existing bug benchmarks for Python, these programs are unpublished and thus not in the language model's training data. In addition, the programs have clear correctness criteria that lead to objective effectiveness metrics." (ChatDBG)

This proactive justification preempts reviewer objections and strengthens the evaluation's credibility.

### Threats to Validity
Include an explicit threats-to-validity subsection that honestly acknowledges limitations of the evaluation. Address representativeness of benchmarks, potential data leakage, stochasticity, and subjective evaluation criteria—then describe specific mitigations for each.

> "LLMs are also inherently stochastic, and it is possible to obtain unusually good results by chance. To mitigate this threat, our evaluation runs ChatDBG on each test program at least ten times." (ChatDBG)

### Adoption Metrics as Evidence
When your tool has real-world adoption, cite it explicitly with concrete numbers. Downloads, GitHub stars, and named industrial users serve as independent validation beyond benchmark numbers.

> "Since its introduction, Scalene has been widely adopted, with over 675,000 downloads to date."

> "Rich, an immensely popular Python library for formatting text in the terminal (downloaded over 130 million times, with 41K stars on GitHub)."

---

## VII. Case Studies and Experience Reports

The Scalene paper introduces a powerful structural element: a dedicated section for real-world case studies from external users. This element goes beyond standard benchmarks by showing how the tool works in the hands of practitioners, not just its authors.

### Structure of a Case Study
Each case study follows a tight narrative:
1. **Context:** Who the user is and what they were doing (named projects and organizations when possible).
2. **Problem:** What performance or resource issue they faced.
3. **Discovery:** What the system revealed (with the system as subject).
4. **Fix:** What the user changed, guided by the tool's output.
5. **Result:** Quantified improvement.
6. **Feature attribution:** Which specific features of the system enabled the finding.

> "A developer was seeing suboptimal performance in their code using Pandas. Scalene identified that a list comprehension performing nested indexes into a Pandas dataframe was taking an unexpectedly large amount of time and resulting in a significant amount of copy volume. ... After manually hoisting this outer indexing operation, the developer obtained an 18x speedup. [Features: Copy volume and fine-grained CPU profiling.]"

### Feature Attribution Tags
End each case study with a bracketed tag listing the features that were instrumental. This tagging links real-world outcomes back to specific technical contributions.

> "[Features: Fine-grained CPU profiling, copy volume.]"

> "[Feature: Fine-grained native vs. Python CPU profiling.]"

### When to Include Case Studies
Case studies are especially valuable for tools intended for broad developer use. They complement synthetic benchmarks by demonstrating:
- That real developers can use the tool effectively without author assistance
- That the tool surfaces actionable insights (not just data)
- That the resulting fixes yield substantial, quantified improvements

---

## VIII. Naming and Framing


### Name Your System
Every paper names its system or technique. The name should be:
- Memorable and pronounceable
- Evocative of what it does (Hoard, DieHard, Exterminator, BLeak, Coz)
- Short (one word preferred)

Once named, the system becomes the protagonist of the paper. It acts, it identifies, it detects, it corrects.

### Coin Memorable Metaphors for Key Concepts
When a technical concept is central to the paper, give it a vivid, memorable name that doubles as both metaphor and technical term. Use this term consistently throughout.

> ChatDBG introduces a "take the wheel" mechanism, where the LLM autonomously issues debugger commands to explore program state.

A good metaphor makes the concept instantly graspable and gives readers a shorthand for discussing your contribution.

### Frame the Problem as Important and Urgent
The opening should make the reader feel that the problem addressed is significant and timely.

- "Applications written in unsafe languages like C and C++ are vulnerable to memory errors... Such errors can lead to program crashes, security vulnerabilities, and unpredictable behavior."
- "Memory leaks remain a serious problem... Leaks degrade responsiveness by increasing GC frequency and overhead, and can even lead to browser tab crashes."

### Challenge Conventional Wisdom
Several of the most impactful papers explicitly overturn established beliefs:
- Reconsidering Custom Memory Allocation challenges the assumption that custom allocators improve performance.
- Coz challenges the assumption that profilers tell you what to optimize.
- DieHard challenges the assumption that memory errors require deterministic detection.

When your work contradicts common practice, state this directly and early.

### Turn Limitations into Advantages
A recurring rhetorical move: identify a known limitation of the platform or prior approach, then show how your system exploits it as a feature.

> "Scalene's CPU profiler turns these limitations of Python signals to its advantage, inferring whether a line spent its time executing Python or native code."

> "The key insight is that this slowdown has the same relative effect as running that line faster, thus 'virtually' speeding it up." (Coz)

This framing transforms a weakness into an insight, making the contribution feel elegant rather than merely incremental.

---

## IX. Conclusion Style

Keep conclusions brief (typically one short page or less). The conclusion should:

1. Restate the contribution in one sentence, with the system as subject.
2. Summarize the key empirical finding.
3. Optionally gesture at future work or broader applicability.

> "This paper presents BLeak, the first effective system for debugging client-side memory leaks in web applications. BLeak has high precision and finds numerous previously-unknown memory leaks in web applications and libraries."

> "This paper presents Scalene, a novel Python profiler. Scalene delivers more actionable information than past profilers, all with high accuracy and low overhead. Its suite of novel algorithms enables Scalene's holistic reporting of Python execution."

Do not introduce new information in the conclusion. Do not repeat the entire paper.

---

## X. General Principles

### Economy of Expression
Every word should earn its place. Cut filler phrases:
- ~~"It is worth noting that"~~ (just state it)
- ~~"In order to"~~ (use "to")
- ~~"Due to the fact that"~~ (use "because")
- ~~"A number of"~~ (use "several" or a specific number)

### Consistent Terminology
Pick one term and stick with it. Do not alternate between synonyms for the same concept. If you call it a "leak root" in Section 3, do not switch to "leak source" in Section 5.

### Define Terms on First Use
Technical terms should be defined precisely when first introduced, often with a brief parenthetical or appositive.

> "...a novel but intuitive metric we call LeakShare..."
> "...progress points, indicating a line in the code that corresponds to the end of a unit of work."

### Introduce Novel Metrics with Clear Motivation
When the paper introduces a new metric, give it a memorable name and immediately explain why it matters. Lead with the problem the metric solves, not the metric itself.

> "Scalene tracks a new metric called copy volume, which highlights costly copying operations that can occur when Python silently converts between native and Python data representations."

> "BLeak ranks leak roots by return on investment using a novel but intuitive metric we call LeakShare."

The pattern: name the metric, then explain what it surfaces that was previously hidden.

### Novel Methodology as a First-Class Contribution
When the paper's primary contribution is a new experimental methodology rather than (or in addition to) a new system, frame the methodology itself as the artifact. Explain clearly why the methodology was previously impossible or impractical, and what it now reveals.

> "This paper presents a tracing and simulation-based experimental methodology that executes unaltered Java programs as if they used explicit memory management." (Quantifying the Performance of Garbage Collection)

The GC paper's "oracular memory manager" is itself the key contribution—a methodology that enables a comparison previously considered infeasible. Name the methodology and treat it as a system.

### Bracketing and Bounding Results
When the true answer lies in a range, use upper and lower bounds to characterize the design space. This technique is more honest and informative than reporting a single point.

> The GC paper uses two oracles—a *liveness* oracle (ideal, unattainable in practice) and a *reachability* oracle (conservative, implementable)—to bracket the performance of explicit memory management. Results from both oracles bound what any real allocator could achieve.

This bracketing technique is especially powerful when comparing paradigms (e.g., GC vs. explicit memory management) where no single experiment captures the full picture.

### Present Results at Meaningful Thresholds
Instead of (or in addition to) continuous curves, report results at specific, memorable resource thresholds that practitioners can map to real deployment decisions.

> "When garbage collection has five times as much memory as required, its runtime performance matches or slightly exceeds that of explicit memory management. However, garbage collection's performance degrades substantially when it must use smaller heaps. With three times as much memory, it runs 17% slower on average, and with twice as much memory, it runs 70% slower."

The 5x/3x/2x framing gives practitioners actionable decision points rather than a curve they must interpret.

### Address Multiple Audiences Explicitly
When results have implications for different communities, address each audience directly in the conclusion or discussion.

> "Practitioners can use these results to guide their choice of explicitly-managed languages like C or C++, or garbage-collected languages like Java or C#." ... "Researchers can use these results to guide their development of memory management algorithms."

This dual-audience framing broadens impact and demonstrates that the work has both practical and scientific value.

### Build Narrative Flow
Each paragraph should connect to the next. The end of one paragraph or section should set up the problem that the next one solves. The reader should never wonder "why am I reading this?"

### Real-World Impact Statements
Whenever possible, note real-world adoption or influence:
- "...the Hoard algorithm was integrated into the Mac allocator."
- "DieHard directly influenced the design of the Windows 7 Fault-Tolerant Heap."
- "Patches for all of these leaks have been submitted to the application developers; at the time of writing, 16 have already been accepted."

This practice grounds the work in practical significance, not just academic novelty.

---

## XI. Checklist for Paper Drafts

- [ ] Does the system (not "we") serve as subject in most technical sentences?
- [ ] Is every sentence in active voice unless there is a specific reason for passive?
- [ ] Are there zero contractions?
- [ ] Does the abstract contain specific numbers?
- [ ] Does the introduction follow the arc: problem, gap, approach, results, contributions?
- [ ] Are contributions explicitly listed with section references?
- [ ] Is there a concrete motivating example?
- [ ] Does the evaluation pose explicit questions?
- [ ] Are results quantified with error bars or significance tests?
- [ ] Is related work placed after the main technical content?
- [ ] Can every figure caption be understood independently?
- [ ] Is every "this" followed by a noun (no bare "this" as pronoun)?
- [ ] Has every filler phrase been eliminated?
- [ ] Is terminology consistent throughout?
- [ ] Does every paragraph connect logically to the next?
- [ ] Would a reader from a different subfield understand the opening paragraph?
- [ ] Do evaluation subsections end with bold **Summary:** takeaways?
- [ ] If the tool has real-world adoption, are download counts or named users cited?
- [ ] Is there a comprehensive feature-comparison table vs. competitors?
- [ ] If applicable, are external case studies included with feature attribution tags?
- [ ] If the system has multiple components, is there an ablation study showing each component's contribution?
- [ ] Does each RQ end with a boxed summary that directly answers the question?
- [ ] If the tool consumes external resources (APIs, compute), are costs reported?
- [ ] Is there an explicit threats-to-validity discussion with mitigations?
- [ ] Are benchmarks justified (provenance, representativeness, no data leakage)?
- [ ] If the methodology is novel, is it framed as a first-class contribution?
- [ ] Are results presented at actionable thresholds, not just as raw curves?
- [ ] If results span a range, are upper and lower bounds used to bracket the answer?
- [ ] Does the conclusion address implications for distinct audiences (practitioners, researchers)?
- [ ] For interactive systems, are extended session transcripts included as figures?
