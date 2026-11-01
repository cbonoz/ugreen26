# Sources and disclosures

## Third-party components and licenses

- UGREEN Skill Developer Package 0.7.3 was the required reference for the standard and capability catalog; its checker was also run locally. The [Starter Kit page](https://ai.ugreen.com/pages/hackathon-starter-kit) links to the [package archive](https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898). There was no LICENSE file or license statement in the archive. No code or assets from it are included here, so its license terms remain unspecified.
- This ZIP includes no third-party libraries, executables, or external downloads.
- The Skill’s runtime dependency is UGREEN Uliya and its registered experts. The public catalog doesn’t identify the model or specify where processing happens, how long data is kept, or detailed permission behavior. The Skill doesn’t select or claim those details.

## Principal functionality developed for this Hackathon

The Hackathon work is a read-only workflow that searches only the user-selected folder, extracts possible obligations, keeps the source passages, separates stated dates from calculated ones, and flags conflicts for review. It doesn’t change files, make payments, or send messages.

## AI tools used in development

- **OpenCode with GPT-6 Luna** helped review the repository and official docs, and helped draft the proposal and Skill. It also helped prepare synthetic fixtures and validate the files.

## Data handling

All test documents are invented. Before processing, the Skill asks the user to confirm they accept the configured Uliya document expert. The public docs don’t explain the model, data location, or retention, so verify those details before using real confidential records. The Skill doesn’t call a separate third-party AI service or API.
