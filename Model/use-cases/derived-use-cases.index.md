# Derived Use Cases from academia.txt

Below is the list of use cases derived from `Model/orm/academia.txt` with goals and links.

| ID     | Title                                     | Goal                                                         | File                                                                                 |
| ------ | ----------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------------------------------ |
| UC-001 | Register New Academic                     | Add a new Academic with a unique employee number and name.   | [use-case-register-new-academic.md](use-case-register-new-academic.md)               |
| UC-002 | Update Academic Name                      | Change an Academic's EmpName while preserving empNr.         | [use-case-update-academic-name.md](use-case-update-academic-name.md)                 |
| UC-003 | Assign Extension to Academic              | Assign an available phone extension to an Academic.          | [use-case-assign-extension-to-academic.md](use-case-assign-extension-to-academic.md) |
| UC-004 | Update Academic Rank                      | Change an Academic’s Rank and ensure ensured AccessLevel.    | [use-case-update-academic-rank.md](use-case-update-academic-rank.md)                 |
| UC-005 | Record Degree and University for Academic | Record that an Academic obtained a Degree from a University. | [use-case-record-degree-and-university.md](use-case-record-degree-and-university.md) |
| UC-006 | Set Academic Employment Status            | Set an Academic as tenured or set a contract end date.       | [use-case-set-employment-status.md](use-case-set-employment-status.md)               |

Notes:

- Ranks map to AccessLevels: P→INT, SL→NAT, L→LOC.
- Constraints enforced via flows/validations per ORM rules.
