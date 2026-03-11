# Qtune Docs Redesign Implementation Plan

> **For agentic workers:** REQUIRED: Use superpowers:subagent-driven-development (if subagents available) or superpowers:executing-plans to implement this plan. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** 将仓库现有的激光钢琴原型文档重构为完整的 `Qtune 光影音乐工作站` 文档体系，覆盖产品、系统、硬件、App、平台、路线图和实施计划。

**Architecture:** 采用“入口文档 + 产品文档 + 技术架构文档 + 交付文档”的四层结构。通过新增明确命名的新文档承接新叙事，并重写旧入口和实施计划，消除旧项目命名、旧路径和过时技术范围。

**Tech Stack:** Markdown, repository docs, internal cross-links

---

## Chunk 1: Audit And Entry Rewrite

### Task 1: Rewrite repository entry

**Files:**
- Modify: `README.md`
- Reference: `docs/superpowers/specs/2026-03-11-qtune-docs-redesign-design.md`

- [ ] **Step 1: Review current README against approved design**

Check current mismatches:
- Still describes `Rust + ESP32` laser piano prototype
- Missing complete product framing
- Missing new doc navigation

- [ ] **Step 2: Write the new README content**

Include:
- `Qtune 光影音乐工作站` title
- product summary
- core value bullets
- system composition
- doc navigation
- version scope

- [ ] **Step 3: Verify README no longer contains old prototype wording**

Run: `rg -n "Laser Piano|激光钢琴|ESP32" README.md`
Expected: no matches, or only deliberate contextual mentions if any remain

## Chunk 2: Add Product Documents

### Task 2: Add product overview

**Files:**
- Create: `docs/product-overview.md`
- Reference: `docs/superpowers/specs/2026-03-11-qtune-docs-redesign-design.md`

- [ ] **Step 1: Draft structure for product overview**

Sections:
- background
- positioning
- target users
- value proposition
- scenarios
- interaction principles

- [ ] **Step 2: Write product overview**

Map PRD narrative content into concise product-facing language.

- [ ] **Step 3: Verify links and naming**

Run: `rg -n "LumiBeats|Laser Piano" docs/product-overview.md`
Expected: no matches

### Task 3: Add PRD document

**Files:**
- Create: `docs/prd.md`
- Reference: `docs/superpowers/specs/2026-03-11-qtune-docs-redesign-design.md`

- [ ] **Step 1: Build PRD outline**

Sections:
- product summary
- hardware specs
- app functions
- platform functions
- UX principles
- non-functional requirements
- technical feasibility
- business model summary

- [ ] **Step 2: Write PRD using approved Qtune naming**

- [ ] **Step 3: Verify terminology consistency**

Run: `rg -n "LumiBeats|Laser Piano" docs/prd.md`
Expected: no matches

## Chunk 3: Add Architecture Documents

### Task 4: Add system architecture

**Files:**
- Create: `docs/system-architecture.md`

- [ ] **Step 1: Define system boundary and actors**

- [ ] **Step 2: Write key flows**

Include:
- calibration
- live performance
- recording
- sync
- content sharing

- [ ] **Step 3: Verify document references align with README**

### Task 5: Add hardware architecture

**Files:**
- Create: `docs/hardware-architecture.md`
- Existing file to leave untouched or deprecate from navigation: `docs/hardware.md`

- [ ] **Step 1: Translate device requirements into architecture sections**

- [ ] **Step 2: Write hardware architecture**

Include:
- projection
- sensing
- compute
- audio
- connectivity
- power
- thermal
- enclosure
- risks

- [ ] **Step 3: Verify no old prototype-only assumptions remain**

### Task 6: Add app architecture

**Files:**
- Create: `docs/app-architecture.md`

- [ ] **Step 1: Define app modules and states**

- [ ] **Step 2: Write app architecture**

Include:
- mode system
- music canvas editor
- rhythm game
- recording and sharing
- device pairing
- account and sync

- [ ] **Step 3: Verify feature names match PRD**

### Task 7: Add platform architecture

**Files:**
- Create: `docs/platform-architecture.md`

- [ ] **Step 1: Define platform content objects**

- [ ] **Step 2: Write platform architecture**

Include:
- users
- templates
- charts
- performances
- feed
- moderation
- creator operations

- [ ] **Step 3: Verify boundaries do not duplicate app architecture**

## Chunk 4: Roadmap And Delivery Docs

### Task 8: Add roadmap

**Files:**
- Create: `docs/roadmap.md`

- [ ] **Step 1: Convert product roadmap into versioned scope**

- [ ] **Step 2: Write roadmap**

Include:
- V1.0
- V1.5
- V2.0
- scope exclusions

- [ ] **Step 3: Verify roadmap matches PRD version language**

### Task 9: Rewrite implementation plan

**Files:**
- Modify: `docs/implementation-plan.md`

- [ ] **Step 1: Review current plan**

Current issue:
- still organized around firmware and ESP32 prototype implementation

- [ ] **Step 2: Rewrite as multi-domain delivery plan**

Include staged work across:
- product definition
- device architecture
- app architecture
- platform architecture
- prototype validation
- content and launch prep

- [ ] **Step 3: Verify implementation plan references new docs**

Run: `rg -n "architecture.md|hardware.md|Laser Piano|ESP32" docs/implementation-plan.md`
Expected: no stale references unless intentionally contextualized

## Chunk 5: Cleanup And Verification

### Task 10: Align links and remove stale navigation

**Files:**
- Modify: `README.md`
- Review: `docs/*.md`

- [ ] **Step 1: Scan for stale names and paths**

Run: `rg -n "Laser Piano|LumiBeats|/home/x/space/LaserPiano|ESP32" README.md docs`

- [ ] **Step 2: Fix remaining stale references**

- [ ] **Step 3: Verify final document set**

Run: `rg --files docs README.md`
Expected:
- `README.md`
- `docs/product-overview.md`
- `docs/prd.md`
- `docs/system-architecture.md`
- `docs/hardware-architecture.md`
- `docs/app-architecture.md`
- `docs/platform-architecture.md`
- `docs/roadmap.md`
- `docs/implementation-plan.md`

- [ ] **Step 4: Commit**

```bash
git add README.md docs
git commit -m "docs: redefine project as Qtune product platform"
```
