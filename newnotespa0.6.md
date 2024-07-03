```mermaid

sequenceDiagram
participant browser
participant server


note right of browser: when the save button is clicked the browser send the user input to the server.It sets the Request Content-type header to JSON
browser->>server:POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa
note right of browser: the server responds with status code 201 created, the note page doesnt reload but just stays on same page
server->>browser: responds with HTTP status code 201

note right of browser: browser execute the event handler in the spa.js code that renders note to the page
