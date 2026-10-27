# Full Stack Open — Part 0

## 0.4: New note diagram

sequenceDiagram
    participant browser
    participant server

   Note over browser: User writes a note and clicks Save
    browser->>server: POST /exampleapp/new_note
    activate server
    Note right of server: Server saves the note
    server-->>browser: 302 Redirect to /exampleapp/notes
    deactivate server

   browser->>server: GET /exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

   browser->>server: GET /exampleapp/main.css
    server-->>browser: CSS file
    browser->>server: GET /exampleapp/main.js
    server-->>browser: JavaScript file

  browser->>server: GET /exampleapp/data.json
    server-->>browser: Updated list of notes

  Note over browser: Browser displays the updated notes

## 0.5: Single page app diagram

sequenceDiagram
  participant browser
  participant server

  browser->>server: GET /exampleapp/spa
  activate server
  server-->>browser: HTML document
  deactivate server

  browser->>server: GET /exampleapp/main.css
  server-->>browser: CSS file
  browser->>server: GET /exampleapp/spa.js
  server-->>browser: JavaScript file
  Note over browser: JavaScript starts executing

  browser->>server: GET /exampleapp/data.json
  activate server
  server-->>browser: JSON containing notes
  deactivate server
  Note over browser: JavaScript displays the notes

## 0.6: New note in single page app diagram

sequenceDiagram
  participant browser
  participant server
  Note over browser: User writes a note and clicks Save
  Note over browser: JavaScript prevents the default form submission
  browser->>server: POST /exampleapp/new_note_spa
  activate server
  Note right of server: Server saves the note
  server-->>browser: 201 Created
  deactivate server
  Note over browser: JavaScript updates the displayed notes
  Note over browser: The page does not reload

