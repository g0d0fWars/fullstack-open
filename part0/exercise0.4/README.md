sequenceDiagram
participant browser
participant server

    Note over browser: User writes text and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over browser,server: Form data sent: note content

    activate server
    Note over server: Server saves the new note
    server-->>browser: HTTP 302 Redirect
    Note over server: Location: /exampleapp/notes
    deactivate server

    Note over browser: Browser follows redirect

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note over browser: Browser executes JS code<br/>that requests note data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data (including new note)
    deactivate server

    Note over browser: Browser renders notes<br/>on the page using JSON data
