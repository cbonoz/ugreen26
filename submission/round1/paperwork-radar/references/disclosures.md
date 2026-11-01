# Disclosures, sources, and development notes

## Components, sources, and licenses

- **UGREEN Skill Developer Package 0.7.3** was used as the required development reference and its bundled checker was run locally. Official sources: [UGREEN Hackathon Starter Kit](https://ai.ugreen.com/pages/hackathon-starter-kit) and [archive](https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898). The archive contained the Uliya Skill Development Standard, capability catalog, references, and checker; no LICENSE file or license statement was present in the archive. Its files/code/assets are not bundled or copied into this Skill package; its license terms remain unspecified.
- No third-party libraries, executable files, or external downloads are included in this Skill package.
- Runtime dependency: UGREEN Uliya and its registered experts/capabilities. The public catalog does not specify a runtime model, service locality, retention, or detailed permission semantics; the Skill does not claim or select them.

## Principal functionality developed for this Hackathon

The original workflow scopes document discovery to one user-selected folder, delegates read-only extraction and reconciliation to the registered Uliya experts, preserves citations, labels explicit versus rule-calculated dates, flags conflicts/uncertainty, and produces a human-reviewed checklist. It performs no file or external side effects.

## AI tools used in development

- **OpenCode with GPT-6 Luna:** repository inspection, reading and interpreting the official package/docs, drafting the proposal and Skill, creating synthetic fixtures, and local validation.
- **TinyFish Search and Fetch:** retrieval of public Devpost/UGREEN contest and developer documentation. No private records were sent; no results from these tools are used as runtime services.

## Data handling

The test corpus is invented and contains no personal or confidential data. The Skill requires disclosure/acceptance of the configured Uliya document expert before processing. Because public documentation does not state the model or data locality/retention, real private or confidential documents must not be used until the user verifies those platform details. No non-UGREEN external AI/API is called by this Skill.
