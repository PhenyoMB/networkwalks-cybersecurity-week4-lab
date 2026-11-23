# M2 | PDF Document Assessment and Password Recovery

This folder contains the evidence for Milestone 2 of the NetworkWalks Week 4 exercise. The objective was to assess the protection applied to the three PDF lab reports identified during the preceding milestone.

> **Sensitive evidence warning:** The screenshots may show patient-style document content, recovered passwords, filenames or other identifying details. Do not publish these images unredacted. The actual document contents and passwords are intentionally omitted from this README.

## 1. Objective

Assess whether the three supplied password-protected exercise PDFs could be opened after offline password recovery. The work was performed against the exercise files, not by attempting to recover passwords for unrelated accounts or systems.

## 2. Tools and process

- **John the Ripper:** Used for offline password recovery after extracting the PDF password hashes.
- **PDF hash extraction utility:** Used to convert the supplied PDF protection data into a format suitable for password-auditing tools.
- **NetworkWalks password tool:** An initial attempt was recorded for the third document; the screenshot set records that this attempt did not succeed.
- **PDF reader:** Used to verify that the recovered passwords opened the exercise documents.

The assessment followed this high-level process:

1. Work with the three PDF files obtained during the exercise.
2. Extract a password hash from each file.
3. Attempt password recovery using the permitted training tools.
4. Record successful and unsuccessful attempts.
5. Verify document access by opening each supplied PDF.
6. Keep recovered passwords and document contents out of public notes.

## 3. Evidence index

| Evidence | Screenshot filename | Recorded activity |
|---|---|---|
| E-12 | 1. patient_report_1.pdf extracted hash.png | Hash extraction for report 1 |
| E-13 | 1.1 patient_record_1_password.png | Password-recovery result for report 1 |
| E-14 | 1.11 patient_record_1_openpdf.png | Report 1 opened successfully |
| E-15 | 2. patient_report_2.pdf extracted hash.png | Hash extraction for report 2 |
| E-16 | 2.1 patient_record_2_password.png | Password-recovery result for report 2 |
| E-17 | 2.11 patient_record_2_openpdf.png | Report 2 opened successfully |
| E-18 | 3.1 patient_record_3_password_cracking_failed_network_walkstool.png | Initial password-recovery attempt did not succeed |
| E-19 | 3.1. patient_report_3.pdf extracted hash.png | Hash extraction for report 3 |
| E-20 | 3.111 patient_record_3_password_cracking_using_john works.png | Successful recovery using John the Ripper |
| E-21 | 3.1111 patient_record_3_openpdf.png | Report 3 opened successfully |

## 4. Outcome

The user reported successful completion of Milestone 2, and the evidence set records successful opening of all three documents. The third document required a different approach after the initial NetworkWalks tool attempt failed; John the Ripper was subsequently used successfully.

The recovered passwords are not included here. Password recovery demonstrates that document-level protection can be undermined when passwords are weak or guessable and an attacker obtains a copy of the protected file.

## 5. Security implications

PDF password protection should not be treated as a substitute for application authorisation. If sensitive documents can be obtained by an unauthorised user, weak document passwords may allow offline recovery without further interaction with the application.

Recommended controls are documented under finding F-02 in the [main M4 report](../README.md). In summary:

- Keep sensitive documents behind server-side access controls.
- Use strong, unique passwords where document encryption is required.
- Use approved modern encryption settings.
- Distribute passwords separately from the protected document.
- Review whether downloading sensitive documents is necessary.
- Avoid storing recovered passwords in screenshots, source control or public reports.

## 6. Evidence handling

Retain original screenshots only in the approved private evidence location. Before any external sharing, redact document contents, patient-style identifiers, passwords, tokens and any other sensitive values. Do not commit the original PDFs or extracted document contents to this repository.

Return to the [main M4 report](../README.md).
