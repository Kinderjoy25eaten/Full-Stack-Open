```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

    user creates a new note :
    Note right of browser: The browser starts executing the JavaScript code that and update the note in text feild.

    browser->>server: post https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    activate server
    Note over browser,server: Payload: { "content": "SPA note", "date": "2026-06-06" }
    server-->>browser: HTTP status code 201 Created (JSON: {"message":"note created"})
    deactivate server

    Note right of browser: The page does not reload! The new note is already visible on the screen.
    

    
