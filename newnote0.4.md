```mermaid

sequenceDiagram
    participant browser
    participant server

    Note over browser: After inputing the note into the text field and clicking the save button, the browser sends the user input to the server
    browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over server: The server returns a 302 status code, which means the server is asking the browser to do a new GET request to the header's location URL
    server-->>browser: responds with HTTP Status Code 302


    Note over browser: the browser reloads the Notes page
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
    Note over server: server responds with text/html content-type
    server-->>browser: HTML code

    Note over browser: the browser request the css file
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Note over server: server responds with text/css content-type
    server-->>browser: main.css

    Note over browser: the browser request the js file
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Note over server: server responds with application/javascript content-type
    server-->>browser: main.js

    Note over browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server-->>browser: [{ content: "wo u woooo u ", date: "2024-07-02T08:00:01.284Z" }, ... ]

    Note over browser: The browser executes the event handler that renders notes to display
