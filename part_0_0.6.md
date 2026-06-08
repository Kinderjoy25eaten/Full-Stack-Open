``` mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: The user writes a note in the text field and clicks the Save button

    Note right of browser: The JavaScript code (spa.js) immediately adds the new note to the local list and redraws the notes on the screen

    browser->>server: POST [https://studies.cs.helsinki.fi/exampleapp/new_note_spa](https://studies.cs.helsinki.fi/exampleapp/new_note_spa)
    activate server
    Note over browser,server: Payload: { "content": "SPA note", "date": "2026-06-06" }
    server-->>browser: HTTP status code 201 Created (JSON: {"message":"note created"})
    deactivate server

    Note right of browser: The page does not reload! The new note is already visible on the screen.
