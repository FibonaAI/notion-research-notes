---
name: notion-research-notes
description: Turn papers, blog posts, and technical materials into accessible, rigorous English close-reading articles, including detailed architecture figure annotations when requested, and publish or update them in Notion when requested. Use for requests such as "summarize this in Notion" or "this week's paper notes," or invoke explicitly to produce a local draft in the same style. Not for general Notion navigation management or unrelated notes.
---

# Notion Research Notes

Keep the explanations, original figures, data, and calculations readers actually need in the main article. The result should stand on its own without chat context. User-approved explanations from the conversation are the content baseline; do not reduce them to an outline when saving or publishing.

## Establish Scope and Sources

- Let the current request determine detail, reader background, page range, number of works, and destination. Default to clear explanations and well-chosen emphasis, but do not omit mechanisms or evidence in the name of accessibility. Do not permanently impose an "80-year-old reader" persona, a 14-page scope, or a fixed number of figures and tables.
- When the user requests page-by-page coverage, organize papers by the specified **physical PDF pages** and state the version, date, and page-number convention. Otherwise, organize around questions, methods, and experiments as appropriate. Follow a blog's natural sections and argument rather than inventing page numbers.
- Check the original paper, official blog, or code. Distinguish source facts, the authors' explanations, your own analysis, and invented teaching examples. Do not mix data from different versions. Explicitly mark inaccessible material instead of presenting invented coverage as something you have read.
- When reading PDFs, use available paper/PDF reading capabilities and check tables and equations against the rendered pages; do not rely solely on extracted text order. Before writing, read the [style and acceptance examples](references/style-guide.md).

## Writing Standards

Open with one sentence explaining what the work does, then identify its sources and scope. Give each page or section a concrete question-based heading and explain its role in the overall argument. Let the material determine length rather than padding to a word count.

- **Methods:** Explain inputs, processing steps, outputs, feedback, selection/update conditions, and the final deliverable. Distinguish prompt changes, parameter training, retrieval, and tool execution. For code-focused requests, identify key functions/files and include short excerpts. Label your own code or pseudocode; never present it as original repository code.
- **Figures:** Prefer relevant original figures, retaining figure numbers, sources, and readable labels. Explain reading order, nodes/arrows, axes, legends, units, dual axes, and differences in scope or measurement across panels. Do not crop away information that affects the conclusion. Label newly drawn supporting figures as "schematic" rather than presenting them as originals.
- **Equations:** Explain the problem first, then symbols and units. Where useful, work through small numerical examples step by step, clearly distinguishing paper data from teaching examples.
- **Experiments:** Retain data tables or legible original tables that support the conclusion; do not substitute "significant improvement." State the model, task/data split, baselines, metric direction, sample size or budget. Calculate important differences and include failures, regressions, and applicability limits.
- **Conclusions:** Distinguish percentage points from relative percentages, individual results from averages, the point at which the best candidate was found from the full budget, and rollout counts from total cost. If the abstract or a caption conflicts with a table, identify the conflict and explain it using verifiable data rather than silently correcting the source.
- End each page/section with a one-sentence takeaway. Close the article with a few central conclusions and limitations. Put search procedures, extraction warnings, and internal indexes only in a closing appendix; do not turn tool logs into the main article unless requested.

## Detailed Architecture Figures

When the user asks to label, mark up, or closely explain a model architecture, dataflow, or timing diagram, read [the architecture annotation workflow](references/architecture-annotations.md). Mark the original figure with numbered callouts and matching explanations, grounded in its caption and nearby methods, equations, or configuration tables. Distinguish training from inference, dataflow from conditioning, illustrative counts from actual configuration, and time from within-step generation or delays where relevant.

Use the same annotation content for the article, figure exports, and optional HTML preview. Inspect every rendered page and verify the actual delivery link or saved file before claiming completion. A request for diagrams alone does not require regenerating the entire article or publishing it to Notion.

## One Canonical Article and Notion Publishing

1. **Maintain one canonical article.** Generate the local report, Notion page, and full explanation for the user from the same finalized text. When an approved answer already exists, preserve all of its paragraphs, tables, figures, worked examples, and limitations. You may correct facts with an explanation, but must not replace the final explanation with an earlier summary. Necessary formatting conversions should not lose content.
2. **Find the authorized destination.** Do not publish externally when the user only requests a local draft. For "this week," check the current date and existing weekly notes in the workspace; do not hard-code a year, week number, or page ID. Look for an existing page for the material and prefer updating it over creating a duplicate. Before updating, read the existing content and protect the user's additions. Modify only blocks relevant to the current request; "update" does not mean replace the whole page. Ask the user when overlapping changes cannot be merged safely.
3. **Preserve weekly records.** Retain the original weekly entries as a chronological log; related research may live in dedicated child pages. Change only the currently authorized scope and do not move or delete unrelated pages. Synchronizing standing topic pages or reorganizing navigation requires explicit current authorization or an established authorization that applies; this skill does not grant broader scope.
4. **Publish usable media and content.** Use configured Notion tools or an authorized signed-in session. Actually upload/attach images to Notion, or use source URLs whose display has been verified. Local absolute paths, `file://`, and `/tmp` are not published images. Convert tables into readable table blocks or a verified equivalent, and keep code and equations legible. Do not leave inaccessible local attachment links in the article. Do not assume a single paste preserves the formatting of a long illustrated article. If size limits or flattened rich text interfere, use supported block-by-block writing or Notion file import, such as a ZIP containing one HTML article and images referenced by relative paths. Confirm the target weekly note before importing, then verify the hierarchy and clean up failed temporary pages created by this operation to avoid duplicate records.
5. **Read back and verify.** After publishing, reread the page, following all pagination and relevant nested child blocks, especially table rows, until completeness is confirmed. Do not mistake a truncated connector response for the full article. Compare against the canonical text item by item: title and page/section scope, paragraphs, table headers and values, figure count/content/order, equations, worked examples, limitations, and sources. Check that uploaded images are actually accessible or render correctly. Matching counts do not prove matching content. Repair truncation, missing blocks, or lost rich text, then verify again.
6. **Report honestly.** Claim "fully written" only after verification and provide the page link. If only part is complete, list what remains. If login, permissions, upload, or rendering is blocked, preserve the complete local draft and explain the blocker; do not bypass permissions or claim success. Stop and ask when the user must intervene to continue.

## Completion Criteria

The article independently explains the method and evidence; source scope is accurate; approved content has not been reduced; and the authorized Notion publication matches the canonical article with usable media. Keep the final reply brief: state the destination, what was preserved, and any unresolved items, without repeating the full article.
