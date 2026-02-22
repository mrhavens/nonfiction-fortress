# Non-Fiction Fortress Level 2
## Research Protocols, Source Databases, and Agent Configurations for Multi-Agent Non-Fiction Writing

---

## Abstract

This paper advances the Non-Fiction Fortress methodology by detailing the operational infrastructure required for multi-agent non-fiction production. We examine genre-specific research protocols, source database architectures, fact-checking agent implementations, citation management systems, expert review workflows, and verification flows. These components transform the conceptual framework from Level 1 into a deployable production system capable of generating verified, publication-ready non-fiction content across diverse genres and subject domains.

---

## 1. Introduction

The foundational methodology established in Level 1 described the roles, workflows, and quality standards essential for credible non-fiction writing. Level 2 operationalizes these concepts into concrete systems and protocols that enable consistent, scalable production.

The transition from methodology to implementation requires addressing several key questions: How do research protocols adapt across genres? What database structures efficiently organize source materials? How do we implement autonomous fact-checking agents? What citation systems ensure academic integrity? How do expert review workflows integrate with automated systems? This paper addresses each of these questions with practical, implementable solutions.

Our approach recognizes that non-fiction is not a monolithic category. A book on quantum physics requires fundamentally different research protocols than a memoir about childhood in rural Montana. The infrastructure must be flexible enough to accommodate these differences while maintaining consistent quality standards.

---

## 2. Detailed Research Protocols for Different Non-Fiction Genres

Non-fiction encompasses numerous sub-genres, each with distinct conventions, source requirements, and verification standards. This section establishes genre-specific research protocols that optimize agent performance across the most common non-fiction categories.

### 2.1 Academic and Educational Non-Fiction

Academic non-fiction demands the highest standards of scholarly rigor. Research protocols for this genre must prioritize primary sources, peer-reviewed publications, and verifiable data.

**Research Protocol: Academic Non-Fiction**

1. **Literature Survey Phase**
   - Search academic databases (Google Scholar, JSTOR, PubMed, arXiv) for foundational papers
   - Identify canonical works and seminal authors in the subject domain
   - Map the intellectual landscape: competing theories, established consensus, open questions

2. **Primary Source Acquisition**
   - Obtain original research papers cited in secondary sources
   - Access official data sets from government agencies, research institutions, or authors
   - Document repository locations and access procedures

3. **Expert Consultation**
   - Identify leading researchers in the field through publication records
   - Prepare specific, targeted questions about contested claims
   - Request clarification on technical terminology and methodological choices

4. **Counterargument Research**
   - Search for critical responses, rebuttals, and replication failures
   - Document fringe or minority positions that merit acknowledgment
   - Note areas of genuine scientific disagreement versus settled consensus

5. **Verification Documentation**
   - Record DOI, URL, access dates, and database names for every source
   - Note peer review status and journal impact factors for academic sources
   - Document any conflicts of interest disclosed by authors

### 2.2 Narrative Non-Fiction and Journalism

Narrative non-fiction blends factual reporting with storytelling techniques. Research protocols must balance rigorous fact-gathering with the immersive detail that makes narrative non-fiction compelling.

**Research Protocol: Narrative Non-Fiction**

1. **Background Research**
   - Compile comprehensive chronological timeline of events
   - Identify key figures, locations, and organizations
   - Gather publicly available documents (court records, press releases, corporate filings)

2. **Source Stratification**
   - **Tier 1**: Direct participants with firsthand knowledge
   - **Tier 2**: Witnesses, journalists who covered events, professional observers
   - **Tier 3**: Secondary accounts, documentaries, archives

3. **Interview Preparation**
   - Develop comprehensive interview protocols for each key source
   - Prepare specific questions that test consistency across sources
   - Identify corroborating evidence needed to verify witness accounts

4. **Document Collection**
   - Photograph or scan physical documents on-site when possible
   - Request official records through appropriate channels (FOIA where applicable)
   - Archive digital sources with timestamp verification

5. **Sensory and Contextual Detail**
   - Research physical locations (weather, geography, atmosphere on relevant dates)
   - Identify period-appropriate details (technology, fashion, language, prices)
   - Note any anachronisms in preliminary drafts

### 2.3 Professional and Business Non-Fiction

Professional non-fiction serves practitioners seeking actionable knowledge. Research protocols must emphasize current best practices, case studies, and expert validation.

**Research Protocol: Professional/Business Non-Fiction**

1. **Industry Landscape Mapping**
   - Identify leading practitioners, consulting firms, and professional associations
   - Map industry publications, trade journals, and professional conferences
   - Note regulatory frameworks and certification requirements

2. **Case Study Research**
   - Identify successful and unsuccessful examples across various contexts
   - Interview practitioners about implementation challenges and lessons learned
   - Document quantifiable outcomes where available

3. **Expert Network Development**
   - Identify thought leaders through speaking engagements, publications, and social media
   - Verify claims through multiple independent expert sources
   - Note dissenting opinions and alternative approaches

4. **Data Gathering**
   - Access industry reports from market research firms
   - Compile government economic data relevant to the field
   - Document statistical sources and methodology notes

### 2.4 Memoir and Personal Narrative

Memoir requires research protocols that support autobiographical accuracy while respecting the inherent subjectivity of personal experience.

**Research Protocol: Memoir**

1. **Memory Verification**
   - Cross-reference personal memories with external sources (photos, letters, public records)
   - Interview family members and contemporaries about relevant events
   - Note discrepancies between memory and documentary evidence

2. **Contextual Research**
   - Research historical events the memoir describes
   - Document cultural, political, and social context of described periods
   - Verify names, dates, locations, and dialogue where possible

3. **Sensitivity Review**
   - Identify living individuals depicted in the narrative
   - Note potentially defamatory or privacy-sensitive content
   - Prepare for legal review of sensitive passages

4. **Authenticity Enhancement**
   - Research period-appropriate language, slang, and cultural references
   - Document sensory details of described locations
   - Note changes in described environments over time

### 2.5 Science and Technology Explainer

Science communication requires research protocols that balance accuracy with accessibility, translating complex concepts for general audiences.

**Research Protocol: Science Explainer**

1. **Primary Literature Review**
   - Read original research papers (not just summaries) for foundational concepts
   - Identify review articles that synthesize multiple studies
   - Note methodological details that affect interpretation

2. **Expert Validation**
   - Consult active researchers (not just science communicators) for technical accuracy
   - Verify that simplifications do not introduce misconceptions
   - Test analogies and explanations with non-expert readers

3. **Scientific Consensus Mapping**
   - Distinguish established consensus from active debates
   - Identify the strength of evidence (single study vs. replicated findings)
   - Note replication crises and contested findings

4. **Visualization Preparation**
   - Identify data that benefits from graphical representation
   - Research existing visualizations for accuracy and clarity
   - Prepare specifications for custom graphics

---

## 3. Source Database Structures and Management

Efficient source management is critical for multi-agent systems. Each agent must be able to access relevant sources quickly, and the system must track the provenance of every piece of information used in the final manuscript.

### 3.1 Database Architecture

We propose a relational database architecture with the following core tables:

**Sources Table**

| Field | Type | Description |
|-------|------|-------------|
| source_id | UUID | Unique identifier |
| title | TEXT | Source title |
| author(s) | TEXT[] | Author names |
| source_type | ENUM | primary, secondary, tertiary, interview, document |
| publication_date | DATE | Publication or creation date |
| publisher | TEXT | Publisher name |
| url | TEXT | Digital location |
| doi | TEXT | Digital Object Identifier |
| access_date | TIMESTAMP | When source was retrieved |
| credibility_score | DECIMAL | 0-1 quality score |
| peer_reviewed | BOOLEAN | Peer review status |
| bias_indicators | JSONB | Documented biases |
| tags | TEXT[] | Subject tags |

**Claims Table**

| Field | Type | Description |
|-------|------|-------------|
| claim_id | UUID | Unique identifier |
| source_id | UUID | Foreign key to sources |
| claim_text | TEXT | Exact claim or data point |
| page_location | TEXT | Page/section reference |
| verification_status | ENUM | unverified, verified, disputed |
| confidence_level | ENUM | high, medium, low |
| notes | TEXT | Analyst notes |

**Quotes Table**

| Field | Type | Description |
|-------|------|-------------|
| quote_id | UUID | Unique identifier |
| source_id | UUID | Foreign key to sources |
| quote_text | TEXT | Exact quotation |
| context | TEXT | Surrounding context |
| page_number | INTEGER | Page reference |
| verified | BOOLEAN | Quote accuracy status |

**Research Sessions Table**

| Field | Type | Description |
|-------|------|-------------|
| session_id | UUID | Unique identifier |
| topic | TEXT | Research topic |
| agent_id | UUID | Agent conducting research |
| start_time | TIMESTAMP | Session start |
| end_time | TIMESTAMP | Session end |
| sources_collected | INTEGER | Count of sources |
| key_findings | TEXT | Summary of discoveries |

### 3.2 Source Organization by Project

Each writing project receives its own database schema with project-specific tags and metadata. This isolation prevents cross-contamination of sources between projects while allowing aggregate analysis across all projects.

**Project-Specific Extensions**

```sql
-- Add project context
CREATE TABLE project_sources (
    source_id UUID REFERENCES sources(source_id),
    project_id UUID REFERENCES projects(project_id),
    relevance_score DECIMAL,
    usage_status ENUM (unused, referenced, cited, quoted),
    PRIMARY KEY (source_id, project_id)
);
```

### 3.3 Source Credibility Scoring Algorithm

The credibility_score field uses a weighted algorithm:

```
credibility_score = (expertise × 0.30) + (1 - bias × 0.25) + (recency × 0.20) + 
                    (reproducibility × 0.15) + (peer_review × 0.10)
```

Where:

- **expertise**: 0-1 based on author credentials, institutional affiliation, publication record
- **bias**: 0-1 based on disclosed conflicts, organizational funding, known ideological positions
- **recency**: 1.0 if <5 years, decreasing for older sources (domain-dependent)
- **reproducibility**: 1.0 if data available, 0.5 if methodology described, 0.25 if neither
- **peer_review**: 1.0 if peer-reviewed, 0.5 if editorial review, 0.25 if neither

### 3.4 Database Management Protocols

**Source Import Protocol**

1. Researcher agent discovers source
2. Agent creates source record with available metadata
3. System attempts auto-fill from CrossRef, ORCID, or other APIs
4. Agent reviews and corrects auto-filled data
5. Agent assigns initial credibility score
6. Source added to project database

**Source Maintenance Protocol**

1. Monthly audit of broken URLs
2. Quarterly review of credibility scores for heavily-cited sources
3. Annual culling of sources below credibility threshold for active projects
4. Archive rather than delete deprecated sources (preserve audit trail)

---

## 4. Fact-Checking Agent Implementation

The Fact-Checker agent represents the critical verification layer in the multi-agent system. This section details implementation approaches for autonomous fact-checking.

### 4.1 Agent Architecture

The Fact-Checker agent operates as a verification pipeline with multiple stages:

```
DRAFT INPUT → EXTRACTION → VERIFICATION → ADJUDICATION → REPORT OUTPUT
```

**Stage 1: Claim Extraction**

The agent parses the draft manuscript and extracts discrete claims requiring verification:

- Factual statements (dates, numbers, locations)
- Quotations (exact text attributed to sources)
- Statistical claims (percentages, comparisons)
- Expert attributions (ideas attributed to named individuals)
- Historical claims (events, causation)

Each extracted claim receives a unique identifier and is mapped to potential verification sources.

**Stage 2: Verification Queries**

For each claim, the agent generates verification queries:

```python
def generate_verification_queries(claim):
    queries = []
    
    # Direct verification
    queries.append({
        "type": "direct",
        "query": f"Verify: {claim.text}",
        "sources": claim.cited_sources
    })
    
    # Independent verification
    queries.append({
        "type": "independent", 
        "query": f"Find independent confirmation of: {claim.text}",
        "sources": get_alternative_sources(claim.topic)
    })
    
    # Context verification
    if claim.is_quote:
        queries.append({
            "type": "context",
            "query": f"Verify quote context: {claim.text[:100]}...",
            "sources": claim.cited_sources
        })
    
    return queries
```

**Stage 3: Adjudication Rules**

The agent applies structured rules to determine verification status:

| Status | Criteria |
|--------|----------|
| **VERIFIED** | Multiple independent sources confirm, exact match to cited source |
| **MOSTLY VERIFIED** | Multiple sources confirm, minor discrepancies in phrasing |
| **UNVERIFIABLE** | No confirming or disproving sources found |
| **DISPUTED** | Conflicting sources exist, no clear resolution |
| **FALSE** | Multiple reliable sources contradict the claim |

**Stage 4: Report Generation**

The agent produces a structured verification report:

```json
{
  "verification_report": {
    "total_claims": 247,
    "verified": 231,
    "mostly_verified": 11,
    "unverifiable": 3,
    "disputed": 1,
    "false": 1,
    "disputed_claims": [
      {
        "claim_id": "c-147",
        "claim_text": "The study showed 40% improvement...",
        "finding": "Original study reported 35%, later reanalysis confirmed 38%",
        "recommendation": "Update to 38% or cite range"
      }
    ],
    "quotes_flagged": [
      {
        "quote_id": "q-089",
        "issue": "Missing ellipsis indicates partial quote",
        "recommendation": "Add ellipsis or provide full context"
      }
    ]
  }
}
```

### 4.2 Confidence Thresholds

The system implements tiered confidence requirements based on claim type:

| Claim Type | Minimum Confidence | Verification Requirement |
|------------|-------------------|-------------------------|
| Direct facts (dates, names) | HIGH | 2+ independent sources |
| Statistics | HIGH | Primary source required |
| Quotations | HIGH | Exact match to source |
| Expert attributions | MEDIUM | Source confirms attribution |
| Generalizations | MEDIUM | Majority of evidence supports |
| Opinion/analysis | LOW | Source identified as opinion |

### 4.3 Dispute Resolution

When verification yields conflicting results, the agent escalates to human review with a structured brief:

1. **Summary**: One-paragraph description of the disputed claim
2. **Evidence For**: Sources supporting the claim
3. **Evidence Against**: Sources contradicting the claim
4. **Source Quality Assessment**: Credibility scores for each source
5. **Recommendation**: Agent's recommendation with confidence level
6. **Options**: Specific revisions that would resolve the dispute

---

## 5. Citation Management Systems

Accurate citation is fundamental to non-fiction credibility. This section details the citation management infrastructure.

### 5.1 Citation Style Configuration

The system supports multiple citation styles with automatic conversion:

**Style Specifications**

| Style | Use Case | Key Features |
|-------|----------|--------------|
| APA 7th | Social sciences | Author-date, references list |
| Chicago 17th | Humanities, journalism | Notes-bibliography or author-date |
| MLA 9th | Literature | Author-page, works cited |
| IEEE | Engineering, computer science | Numbered brackets |
| Bluebook | Legal | Complex legal citation rules |

**Style Adapter Module**

```python
class CitationAdapter:
    def __init__(self, style="chicago"):
        self.style = style
        self.formatters = {
            "chicago": self.format_chicago,
            "apa": self.format_apa,
            "mla": self.format_mla,
            "ieee": self.format_ieee
        }
    
    def format(self, source, citation_type="bibliography"):
        formatter = self.formatters.get(self.style)
        return formatter(source, citation_type)
    
    def format_chicago(self, source, citation_type):
        # Implement Chicago style formatting
        if citation_type == "bibliography":
            return f"{source.author}. {source.title}. {source.publisher}, {source.year}."
        elif citation_type == "footnote":
            return f"{source.author}, {source.title} ({source.year}), {source.page}."
```

### 5.2 Citation Tracking Pipeline

**Integration Points**

1. **Research Phase**: Citations tracked when sources are added to database
2. **Drafting Phase**: Writer agent inserts citation placeholders
3. **Verification Phase**: Fact-checker validates citation accuracy
4. **Formatting Phase**: Citation adapter converts to target style
5. **Final Review**: Editor confirms citation consistency

**Citation Database Schema**

```sql
CREATE TABLE citations (
    citation_id UUID PRIMARY KEY,
    source_id UUID REFERENCES sources(source_id),
    chapter_id UUID,
    paragraph_id UUID,
    citation_type ENUM (bibliography, footnote, endnote, inline),
    formatted_text TEXT,
    style_used TEXT,
    verification_status ENUM (pending, verified, incorrect),
    UNIQUE(source_id, chapter_id, paragraph_id)
);
```

### 5.3 Citation Quality Assurance

**Automated Checks**

- **Duplicate detection**: Identify multiple citations of same source
- **Style consistency**: Verify uniform formatting throughout
- **Completeness audit**: Flag missing required fields for style
- **Dead link detection**: Check URLs still resolve
- **DOI validation**: Verify DOIs resolve correctly

**Manual Review Triggers**

The system flags for human review:

- Citations with missing or incomplete source data
- Citations to sources with credibility scores below threshold
- Citations where verification found discrepancies
- First citation of each source (manual verification recommended)

---

## 6. Expert Review Workflows

Human expertise remains essential for non-fiction quality. This section details workflows that integrate expert review with automated systems.

### 6.1 Expert Identification and Recruitment

**Identification Criteria**

1. **Subject Matter Expertise**: Advanced degree or extensive professional experience in relevant field
2. **Communication Ability**: Track record of explaining complex topics accessibly
3. **Availability**: Reasonable response time and willingness to review
4. **Conflict Screening**: No significant conflicts of interest with topic

**Expert Database**

```sql
CREATE TABLE experts (
    expert_id UUID PRIMARY KEY,
    name TEXT,
    credentials TEXT[],
    affiliations TEXT[],
    expertise_areas TEXT[],
    publication_count INTEGER,
    availability_status ENUM (available, busy, unavailable),
    preferred_review_format ENUM (full_manuscript,章节,段落),
    contact_information JSONB
);
```

### 6.2 Review Assignment Protocol

**Tiered Review Structure**

| Tier | Reviewer | Focus | Timing |
|------|----------|-------|--------|
| Tier 1 | Subject expert | Factual accuracy, technical correctness | Post-draft, pre-editing |
| Tier 2 | Industry practitioner | Practical applicability, real-world relevance | Post-first revision |
| Tier 3 | Beta readers | Engagement, clarity, audience response | Final draft |

**Assignment Algorithm**

1. Extract key topics and concepts from manuscript
2. Match to expert database by expertise areas
3. Filter by availability and conflict of interest
4. Rank by relevance score and credibility indicators
5. Generate invitation with specific review questions

### 6.3 Review Integration

**Structured Feedback Format**

Experts provide feedback in standardized format:

```json
{
  "expert_review": {
    "expert_id": "exp-001",
    "review_date": "2024-03-15",
    "manuscript_version": "2.1",
    "accuracy_concerns": [
      {
        "location": "Chapter 3, Page 42",
        "issue": "Description of mechanism is outdated",
        "severity": "high",
        "suggestion": "Update to reflect 2023 research",
        "supporting_source": "DOI:10.xxxx/example"
      }
    ],
    "omissions": [
      {
        "topic": "Recent developments in X",
        "importance": "medium",
        "suggested_addition": "Include reference to 2024 breakthrough"
      }
    ],
    "clarity_issues": [
      {
        "location": "Chapter 5",
        "issue": "Technical explanation assumes too much background",
        "suggestion": "Add brief definition of key term"
      }
    ],
    "overall_assessment": {
      "accuracy": "good_with_revisions",
      "completeness": "adequate",
      "clarity": "good",
      "recommendation": "publish_after_revisions"
    }
  }
}
```

### 6.4 Revision Workflow

**Feedback Integration Pipeline**

1. Editor reviews expert feedback
2. Editor prioritizes changes (critical, recommended, optional)
3. Writer agent implements changes
4. Fact-checker verifies revised claims
5. Editor reviews implementation
6. Expert confirms resolution (for critical issues)

**Version Control**

All revisions tracked with full audit trail:

```sql
CREATE TABLE revisions (
    revision_id UUID PRIMARY KEY,
    manuscript_version VARCHAR,
    change_type ENUM (addition, deletion, modification),
    location TEXT,
    previous_text TEXT,
    new_text TEXT,
    rationale TEXT,
    feedback_source VARCHAR,
    implemented_by VARCHAR,
    timestamp TIMESTAMP
);
```

---

## 7. Example Research Queries and Verification Flows

This section provides concrete examples demonstrating the complete research-to-verification pipeline.

### 7.1 Example: Science Explainer Research Query

**Topic**: "The Development of mRNA Vaccine Technology"

**Research Query Sequence**

```
QUERY 1: "mRNA vaccine history development timeline"
  Sources: PubMed, Google Scholar
  Goal: Establish chronological foundation
  
QUERY 2: "Katalin Karikó mRNA research contributions"
  Sources: Academic papers, interviews, biographies
  Goal: Identify key figures and their contributions

QUERY 3: "mRNA vaccine mechanism of action"
  Sources: Primary research papers, review articles
  Goal: Verify technical accuracy of explanation

QUERY 4: "COVID-19 mRNA vaccine clinical trial results efficacy"
  Sources: FDA documents, NEJM publications
  Goal: Obtain precise statistics

QUERY 5: "mRNA vaccine safety profile adverse reactions"
  Sources: CDC, FDA, peer-reviewed studies
  Goal: Balance efficacy with risk information

QUERY 6: "mRNA vaccine technology controversies misinformation"
  Sources: Fact-checking organizations, scientific consensus statements
  Goal: Address common misconceptions
```

**Verification Flow for Key Claim**

*Claim extracted*: "The COVID-19 mRNA vaccines showed 95% efficacy in initial clinical trials."

```
VERIFICATION STAGE 1: Direct Source Check
  → Retrieved: NEJM publication, DOI: 10.1056/NEJMoa2034577
  → Finding: Phase 3 trial showed 95% efficacy (95% CI: 90.3-97.6)
  → Status: VERIFIED (exact match)

VERIFICATION STAGE 2: Independent Confirmation  
  → Retrieved: FDA briefing document
  → Finding: Confirmed 95% efficacy estimate
  → Status: VERIFIED

VERIFICATION STAGE 3: Context Check
  → Note: Efficacy varied by variant and time since vaccination
  → Recommendation: Add qualifier about variant dependence
  → Status: MOSTLY VERIFIED (needs context)
```

### 7.2 Example: Narrative Non-Fiction Verification Flow

**Topic**: "The Rescue of the Chilean Miners (2010)"

**Research Query Sequence**

```
QUERY 1: "Chilean miners rescue 2010 timeline"
  Sources: News archives (NYT, BBC, Chilean newspapers)
  Goal: Establish accurate chronology

QUERY 2: "Chile mine collapse Atacama details"
  Sources: Official reports, geological surveys
  Goal: Verify technical details

QUERY 3: "Mario Gómez miner interview experiences"
  Sources: Direct interviews, documentary footage
  Goal: First-hand account verification

QUERY 4: "Minister Golborne Chile mining rescue role"
  Sources: Government records, news coverage
  Goal: Verify official actions and statements
```

**Quote Verification Flow**

*Quote attributed to miner Luis Urzúa*: "We were prepared to wait 30 days. We had no idea it would be 70."

```
VERIFICATION STAGE 1: Source Location
  → Primary source: PBS documentary "The 33"
  → Timestamp: 42:15
  → Context: First communication after collapse

VERIFICATION STAGE 2: Cross-Reference
  → Secondary source: ESPN article quoting Urzúa
  → Finding: Similar quote, slight variation in wording
  → Note: Exact quote may be paraphrase

VERIFICATION STAGE 3: Context Verification
  → Checked: Was 30 days the official estimate?
  → Finding: Mining company initially estimated 3-4 months
  → Discrepancy: Urzúa may have said "we prepared for 30 days" personally

RECOMMENDATION: Flag as approximate quote, add clarification
STATUS: MOSTLY VERIFIED WITH CAVEAT
```

### 7.3 Complex Multi-Source Verification

**Claim**: "The 2008 financial crisis caused 10 million Americans to lose their homes."

```
VERIFICATION STAGE 1: Define Terms
  → "Lost homes" = Foreclosures, short sales, distressed sales
  → Timeframe: 2008-2014 (crisis and aftermath)
  → Source definition matters significantly

VERIFICATION STAGE 2: Source Collection
  → Source A: Center for Responsible Lending - 9.3 million foreclosures
  → Source B: RealtyTrac - 7.3 million foreclosure sales
  → Source C: Pew Research - 11 million homeowners underwater
  
VERIFICATION STAGE 3: Adjudication
  → Different methodologies yield different numbers
  → No single "correct" figure exists
  → Claim requires qualification

REVISED CLAIM (recommended): 
  "The 2008 financial crisis led to approximately 9-11 million 
   homeowners losing their homes to foreclosure, with millions more 
   experiencing underwater mortgages."

STATUS: UNVERIFIABLE AS STATED (requires range/qualification)
```

---

## 8. System Integration and Workflow Orchestration

### 8.1 Complete Production Pipeline

The complete system integrates all components into a unified production pipeline:

```
┌─────────────────────────────────────────────────────────────────┐
│                     RESEARCH PHASE                              │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │Researcher│───▶│ Analyst  │───▶│ Database │                  │
│  │  Agent   │    │  Agent   │    │ Manager  │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│       │              │                  │                       │
│       ▼              ▼                  ▼                       │
│  Source Dossier  Framework      Source Database                 │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                     DRAFTING PHASE                              │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │  Writer  │◀───│  Voice   │◀───│ Research │                  │
│  │  Agent   │    │Calibrator│    │ Database │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│       │                                                      │
│       ▼                                                      │
│  Draft Manuscript                                            │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                   VERIFICATION PHASE                           │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │   Fact   │───▶│ Citation │───▶│  Expert  │                  │
│  │ Checker  │    │ Manager  │    │ Review   │                  │
│  │  Agent   │    │          │    │Workflow  │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│       │              │                  │                       │
│       ▼              ▼                  ▼                       │
│  Verification    Citation         Expert                        │
│     Report        Database       Feedback                      │
└─────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────────┐
│                     REVISION PHASE                              │
│  ┌──────────┐    ┌──────────┐    ┌──────────┐                  │
│  │  Writer  │◀───│  Editor  │◀───│ Revisions│                  │
│  │  Agent   │    │  Agent   │    │ Database │                  │
│  └──────────┘    └──────────┘    └──────────┘                  │
│       │                                                      │
│       ▼                                                      │
│  Revised Manuscript                                          │
└─────────────────────────────────────────────────────────────────┘
```

### 8.2 Quality Gates

Each phase includes quality gates that must be passed before proceeding:

| Gate | Criteria | Escalation |
|------|----------|------------|
| Research Complete | All key topics covered, minimum source threshold met | Extend research |
| Draft Acceptable | All sections written, voice consistent | Revision pass |
| Verification Passed | All critical claims verified, disputed items resolved | Expert review |
| Editorial Approved | Structure, clarity, style meet standards | Final revision |
| Expert Sign-Off | Accuracy confirmed by subject experts | Address concerns |

---

## 9. Conclusion

This paper has detailed the operational infrastructure required to implement the Non-Fiction Fortress methodology established in Level 1. We have covered:

1. **Genre-specific research protocols** that optimize research approaches for academic, narrative, professional, memoir, and science communication non-fiction
2. **Source database structures** that efficiently organize source materials with credibility scoring and relationship tracking
3. **Fact-checking agent implementation** that provides autonomous verification with structured adjudication rules
4. **Citation management systems** that ensure academic integrity through style configuration and quality assurance
5. **Expert review workflows** that integrate human expertise into the automated pipeline
6. **Example verification flows** demonstrating the complete research-to-publication process

These components together create a production system capable of generating verified, publication-ready non-fiction across diverse genres. The infrastructure maintains the rigorous standards essential for credible non-fiction while enabling the efficiency benefits of multi-agent collaboration.

Future work will explore:

- Real-time source updating for time-sensitive topics
- Automated detection of emerging misinformation
- Integration with publishing platform APIs
- Advanced visualization generation for data-heavy content
- Multi-language research and verification capabilities

The Non-Fiction Fortress system represents a significant advancement in AI-assisted non-fiction production, combining the speed and scalability of automated systems with the rigor and judgment required for authoritative publishing.

---

*Level 3 will address advanced topics including multi-project portfolio management, adaptive learning systems, and deployment scaling strategies.*

---

**Document Information**

- Title: Non-Fiction Fortress Level 2: Research Protocols, Source Databases, and Agent Configurations
- Word Count: ~4,200 words
- Dependencies: Requires Level 1 foundational methodology
- Next: Level 3 - Advanced Systems and Scaling