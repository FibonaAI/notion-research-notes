# Detailed Architecture Figure Annotations

Use this workflow when the user asks to label, mark up, or closely explain model architecture, dataflow, or timing diagrams. The result should let a reader locate a component in the original figure and understand its role without returning to the chat. Select the figures needed for the request; the Moshi example below is not a fixed figure or annotation count.

## Establish the Evidence

1. Locate the original figures and inspect their rendered pages. Record the paper version, physical PDF page, figure number, and relevant caption, equations, tables, or implementation references. Extracted text alone does not establish arrow direction or spatial relationships.
2. Read the nearby method description before labeling. Check simplified diagrams against the actual configuration, especially omitted layers, illustrative stream counts, and special treatment of the first output. Preserve a discrepancy between a schematic and the equations rather than silently inventing a consistent diagram.
3. Map the input, transformations, intermediate representations, outputs, feedback, and training supervision. For each proposed annotation, keep a source pointer and distinguish source facts from teaching explanations or unresolved interpretation. Omit unsupported dimensions, parameter counts, loss functions, or causal claims.
4. When working in a browser, use the authorized viewer and keep the source PDF available. Obtain a local copy only when needed by the export tools. A title or an unread URL is not sufficient evidence.

## Make the Markings Explain the Mechanism

Put numbered markers and short leader lines on the actual figure, with matching explanations beside or below it. A caption highlight or a prose summary alone does not satisfy a request to mark the architecture. If the viewer supports only text highlights, produce a separate annotated figure or document and describe accurately where the detailed annotations live.

Explain the following when the source supports them:

| Area | What the reader should be able to answer |
|---|---|
| Modules and arrows | What enters this module, what operation occurs, what leaves it, and where does the result go? Is an arrow dataflow, conditioning, feedback, or a training objective? |
| Representations | Is this a waveform, feature vector, text token, semantic code, acoustic code, or probability distribution? Which rate, dimension, unit, or codebook cardinality applies? |
| Training and inference | Which parts run during interaction? Which teachers, losses, discriminators, or ground-truth inputs belong to training? Distinguish generated values from observed inputs. |
| Generation order | Which axis advances time, depth, layers, or token streams? What is already known when each prediction is made? Explain special cases such as a separate first-token head. |
| Timing | Which indices refer to the same source frame? Show delays explicitly; visually aligned rows may refer to different frames. Distinguish theoretical streaming latency from measured latency and conversational response time. |
| Simplifications | Which counts or blocks are illustrative? Where does the full model differ? Label supplementary teaching diagrams as schematics. |

Keep notes specific to the referenced location. A useful note combines **name → operation → input/output or dependency → important boundary**, rather than expanding only an acronym. Use color consistently and also use numbers or text so color is not the only identifier.

## Preserve Legibility and One Source of Content

- Keep the original labels, relevant legend, and arrowheads legible. Crops must retain information needed to interpret the figure. Put leader endpoints on module borders or clear space when a center point would obscure text. Avoid crossing labels, equations, or other callouts.
- Place longer explanations outside the original drawing. Split dense figures across pages or enlarge them instead of shrinking the labels beyond readability. Choose the layout for the figure; landscape pages are useful but not mandatory.
- Preserve vector content when practical, or use a sufficiently sharp crop. Embed a font that supports the requested language. Do not use generative image editing to reconstruct scientific labels or equations.
- For multiple exports, keep a shared annotation list containing figure/page identity, source/crop coordinates, marker ID, target location, title, explanation, and evidence. Specify whether coordinates are PDF points or normalized within a crop. Generate the PDF, image previews, and text explanations from this same list so numbering and wording cannot drift.
- Keep the source intact and label the added explanation as a reading annotation. Store outputs separately from the source PDF.

## Verify the Artifact and the Delivery

Render every annotated page and inspect the result after layout changes. Check that each marker has the intended target and exactly one matching explanation, original labels remain visible, notes are not clipped, fonts render correctly, and timing indices and quantitative claims match the source. Matching page or marker counts alone do not prove correctness.

Deliver an annotated PDF or image set in the format the user requested. When browser reading is useful or the PDF viewer fails, offer a simple HTML preview with full-size images and readable text explanations. A zoom control and expandable notes can help with dense pages. For offline use, embed the images or package them with relative paths; verify that the exported file does not depend on a temporary preview server. Offline navigation and download links should resolve to bundled files, or server-only controls should be omitted from the offline copy.

Test the actual delivery route, not only file creation: open the link in the user's available browser or application, inspect visible content, and confirm downloaded files are complete. A loopback server URL is a temporary local preview, not a durable public link. Retain a saved offline artifact. If a preview is stuck, use a different supported format rather than repeatedly issuing the same blocked action; state which view has been verified.

If publishing to Notion or another destination is requested, upload the annotated media using that destination's supported mechanism and check the displayed result. Do not publish local filesystem paths or loopback URLs as remote image sources. This annotation workflow does not authorize publishing or changing unrelated content.

## Worked Reference: Moshi

The Moshi reading session illustrates the level of detail to aim for, not model facts to copy into future reports. Its four selected figures received 36 numbered notes; different material may need fewer or more.

| Original figure | Example of the distinction the annotations must explain |
|---|---|
| [Figure 1, page 7](https://arxiv.org/pdf/2410.00037v2#page=7&search=Overview%20of%20Moshi&phrase=true) | Trace user audio through Mimi, history embeddings, temporal context, text/audio generation, and the output decoder. |
| [Figure 2, page 10](https://arxiv.org/pdf/2410.00037v2#page=10&search=Architecture%20and%20training%20of%20Mimi&phrase=true) | Separate semantic VQ from acoustic RVQ and distinguish the causal runtime path from teacher/loss branches used for training. |
| [Figure 3, page 13](https://arxiv.org/pdf/2410.00037v2#page=13&search=Architecture%20of%20the%20RQ-Transformer&phrase=true) | Distinguish the time axis from within-step generation, the illustrative K=4 from the full 17-stream representation, and the first-token linear head described in the equations. |
| [Figure 4, page 15](https://arxiv.org/pdf/2410.00037v2#page=15&search=Representation%20of%20the%20joint%20sequence%20modeled%20by%20Moshi&phrase=true) | Show that a column can contain current semantic tokens and delayed acoustic tokens. Explain the 80 ms frame and one-frame acoustic delay behind the theoretical 160 ms figure, with support from Sections 3.4.2–3.4.4. |

Reuse the pattern: **original figure → located marker → evidence-backed explanation → misunderstood dependency or boundary → verified, readable export**. Recheck the source for every new paper or version.
