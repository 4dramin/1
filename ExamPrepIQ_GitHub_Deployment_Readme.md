# Dr. Amin ExamPrep IQ — GitHub Pages publication guide

## Official deployment

Publish **ExamPrepIQ_100_Mocks_Protected_GitHub_Pages.html** as **index.html** in the root of the GitHub Pages project at **https://4dramin.github.io/1/**. The protected version is deliberately bound to that HTTPS origin and `/1/` path, so it will NOT run from `file://`, localhost, or a different GitHub Pages account or project. To test, upload it to the intended live URL.

## What this protection does

- Encrypts the 100-exam active content bank and the mock-bank startup script using AES-256-GCM. No student questions or passages are directly readable in that part of View Source.
- Checks the encrypted sections for modification, and refuses to initialize if they fail the check.
- Limits the exam unlock to the authorized GitHub Pages site.
- Keeps your name in the footer, visible ownership notice, metadata, and original watermark; restores the visible footer/watermark if removed while the authorized page is running.
- Includes a release SHA-256 manifest to help you verify your own file has not changed.

## A crucial technical limitation

This protection does NOT make public HTML uneditable or undecipherable. Code and decryption logic used by a public browser are available to a sufficiently motivated person, who can copy or modify them and bypass client-side checks. It is **not** real server-side DRM.

For enforceable protection, maintain the content in a private repository or server, deliver it only after authenticated authorization from a trusted backend, and use limited-lived access credentials. Even that cannot prevent a student from transcribing material they can view.

## Protect your real GitHub publication

1. Enable GitHub two-factor authentication/passkeys; avoid giving write access to collaborators without need.
2. Enable branch protection / rulesets, restrict who can push or deploy, and require pull requests for changes.
3. Use a release tag and the `ExamPrepIQ_GitHub_Release_Integrity.json` digest to confirm the exact authorized release.
4. Keep your editable original HTML and teacher answer-key PDFs out of the publicly deployed repository.
5. Keep the Student and Teacher PDFs separate; never publish the teacher answer-key files on the same public site if students should not see them.
6. Display the copyright notice; publish clear reuse terms and maintain authorship records.
7. If a third-party copies your content, pursue the platform's copyright-reporting procedure; technical watermarks alone are not a substitute for enforcement.

## SHA-256 (expected exact file)

`bfed48460f9b593581677acbbdbc6a9f7699455c7ea4efcb50949a8b9af2b624`

## Updating content in the future

Always edit your original master HTML and rebuild the protected version. Editing the encrypted release directly will fail its checks. Because the build uses newly generated encryption material, its encrypted hashes will change at every rebuild.

**Keep the editable original secure.** This protected release is for publishing, not for maintaining the question bank.
