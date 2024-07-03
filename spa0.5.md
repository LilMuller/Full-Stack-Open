```mermaid

sequenceDiagram
  participant browser
  participant server

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
server->>browser: HTML code without the notes data

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
server->>browser: main.css (the css file)

browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
server->>browser: spa.js

note right of browser: browser start executing the javascript code which request for the data.json from the server
browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
server->>browser: [{content: "pruebbbbba",date: "2024-07-03T07:04:58.388Z"}, ...]

note right of browser: browser start executing the event handler in spa.js code which renders the notes to display
