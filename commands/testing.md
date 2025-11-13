# Testing Command

## General

*   Tests: **isolated, deterministic, fast**.
*   Naming: `test_<feature>.py`, `Component.test.ts`.
*   Assert **behavior**, not implementation.
*   No “what” comments; only **why** if needed.
*   Must run same **locally & CI**.

## Python

*   Enter env:
    ```bash
    poetry shell
    ```

## UI / Frontend

*   One `describe` per file; multiple `it` inside.
*   Tests = **specs**, not docs.
*   Focus on **user scenarios**, not internals.
*   Keep concise, consistent, predictable.
