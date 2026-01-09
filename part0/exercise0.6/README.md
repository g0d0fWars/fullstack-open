sequenceDiagram
participant browser
participant server

    Note over browser: User writes text in input field<br/>and clicks Save button

    Note over browser: Event handler calls e.preventDefault()<br/>to prevent default form submit behavior

    Note over browser: JavaScript creates a new note object<br/>with content and date properties

    Note over browser: New note is added to notes array<br/>with notes.push(note)

    Note over browser: JavaScript rerenders the note list<br/>by updating the DOM

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
    Note over browser,server: Content-Type: application/json
    Note over browser,server: Request body: {"content": "test", "date": "2024-1-1"}

    activate server
    Note over server: Server parses JSON data and saves the note
    server-->>browser: 201 Created
    deactivate server

    Note over browser: Browser stays on the same page<br/>No further HTTP requests are sent
