# Sources and disclosures

## Third-party components and licenses

- We used UGREEN Skill Developer Package 0.7.3, as required, to read the standard and capability catalog and run its checker. The [Starter Kit page](https://ai.ugreen.com/pages/hackathon-starter-kit) links to the [package archive](https://cdn.shopify.com/s/files/1/0630/9416/1602/files/uliya-skill-kit-0.7.3-en.zip?v=1790578898). The archive had no LICENSE file or license statement. We didn’t copy its code or assets into this Skill, so its license terms remain unspecified here.
- This ZIP includes no third-party libraries, executables, or external downloads.
- The Skill’s runtime dependency is UGREEN Uliya and its registered experts. The public catalog doesn’t identify the model or specify where processing happens, how long data is kept, or detailed permission behavior. The Skill doesn’t select or claim those details.

## Principal functionality developed for this Hackathon

The new work for this Hackathon is a read-only workflow: search only the user-selected folder, extract possible obligations, keep the source passages, separate stated dates from calculated ones, and flag conflicts for the user to review. It doesn’t change files or make payments or send messages.

## AI tools used in development

- **OpenCode with GPT-6 Luna** helped inspect the repository and official docs, draft the proposal and Skill, prepare synthetic fixtures, and check the files.
- **TinyFish Search and Fetch** retrieved public Devpost and UGREEN rules and documentation. No private records were sent, and neither tool is part of the Skill’s runtime.

## Data handling

All test documents are invented. Before processing, the Skill asks the user to confirm they accept the configured Uliya document expert. Since the public docs don’t explain the model, data location, or retention, don’t use real confidential records until those details are checked. The Skill doesn’t call a separate third-party AI service or API.
