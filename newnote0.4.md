```mermaid

sequenceDiagram
    participant browser
    participant server

    Note right of browser: After inputing the note into the text field and clicking the save button, the browser sends the user input to the server
    browser->>server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note left of server: The server returns a 302 status code, which means the server is asking the browser to do a new GET request to the header's location URL
    server-->>browser: responds with HTTP Status Code 302


    Note right of browser: the browser reloads the Notes page
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
    Note left of server: server responds with text/html content-type
    server-->>browser: HTML code

    Note right of browser: the browser request the css file
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Note left of server: server responds with text/css content-type
    server-->>browser: main.css

    Note right of browser: the browser request the js file
    browser->>server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Note left of server: server responds with application/javascript content-type
    server-->>browser: main.js

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    server-->>browser: [{ content: "wo u woooo u ", date: "2024-07-02T08:00:01.284Z" }, ... ]

    Note right of browser: The browser executes the event handler that renders notes to display
