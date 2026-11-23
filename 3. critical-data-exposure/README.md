# M3 | Critical Data Exposure and Metadata Review

This folder contains the evidence for Milestone 3 of the NetworkWalks Week 4 exercise. The investigation followed a clue identified during the review of the three PDF reports and led to a legacy location associated with database-related material.

> **Sensitive evidence warning:** The screenshots in this folder are explicitly labelled as showing staff and shareholder information. They may contain personal, financial, database or other confidential training data. They are not embedded in this README. Keep the originals private and redact them before any external sharing.

## 1. Objective

Review the properties and embedded information in the exercise documents, identify the additional location indicated by the document evidence, and establish whether database-related or other sensitive information was exposed.

## 2. Investigation summary

The exercise involved:

1. Reviewing PDF metadata and document properties using ExifTool.
2. Examining readable strings and embedded comments in the supplied PDFs.
3. Identifying a comment/metadata clue in one of the documents.
4. Following the clue to an old or legacy location associated with database-related material.
5. Reviewing the exercise evidence for staff and shareholder information at that location.

The main M4 report intentionally does not reproduce the comment value, sensitive URL, database contents, staff names, salary figures, shareholder details, credentials or other confidential values.

## 3. Evidence index

| Evidence | Screenshot filename | Recorded activity |
|---|---|---|
| E-22 | 1. cde exiftool metadata.png | PDF metadata inspection |
| E-23 | 2. cde strings shows that there's a comment on one of the files thats hidden.png | Identification of an embedded comment in a document |
| E-24 | 3. cde decrypt all 3 files.png | Exercise documents processed for metadata review |
| E-25 | 4. cde shows db backup moved to old before migration.png | Evidence of a database backup/legacy-location clue |
| E-26 | 5. cde checking the domain name of old and finding data.png | Review of the old/legacy location |
| E-27 | 6. cde finding staff information.png | Staff information exposure recorded |
| E-28 | 7. cde finding shareholder information.png | Shareholder information exposure recorded |

## 4. Outcome

The user reported successful completion of Milestone 3 and discovery of database-related information. The evidence folder records a legacy backup clue and subsequent discovery of staff and shareholder information.

The exact exposure mechanism should be described precisely in the tutor-facing version of the report using the original evidence. The current repository notes do not establish whether the material was exposed through directory listing, a directly accessible backup file, an old application route or another configuration issue. This README therefore describes it as a legacy-location/sensitive-information exposure rather than assigning an unverified technical root cause.

## 5. Security implications

Legacy directories, migration artefacts and database backups can unintentionally remain accessible after systems are moved or updated. If access controls are not applied consistently, these resources can expose business records and information that should only be available to authorised personnel.

The exposure of staff and shareholder information may create privacy, financial, regulatory and reputational consequences. If credentials or database exports are present in the exposed material, the potential impact may be broader.

## 6. Recommended remediation

- Remove database backups and exports from public web directories.
- Store backups in a separate, access-controlled storage location.
- Disable directory listing and explicitly deny public access to backup, migration and archive paths.
- Review old domains, aliases, virtual hosts and legacy directories during decommissioning.
- Apply least-privilege permissions to backup files and database exports.
- Rotate any credentials that may have been included in exposed files.
- Review server and application logs for access to the affected location.
- Remove unnecessary metadata and embedded comments before distributing documents.
- Establish backup retention, access review and secure-deletion procedures.

See finding F-03 in the [main M4 report](../README.md) for impact and prioritised recommendations.

## 7. Evidence handling

Do not include unredacted screenshots of staff, shareholder or database information in public repositories, social posts or public reports. Keep the original evidence in the approved private location and share it only with the tutor or authorised assessor.

Return to the [main M4 report](../README.md).
