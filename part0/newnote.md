Here is a simple flow chart:

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note left of browser: The user fills in note form and submits a new note
    browser-->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/notes
    Note left of browser: Browser sends a POST request containing note data in the request body
    activate server
    Note right of server: Server adds the new note to the notes array
    server-->>browser: HTTP 302 status code - redirect back to /notes page
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML-code for /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: main.css
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: main.js
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes
```
