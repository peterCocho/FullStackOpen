# Sequence diagram showing how a note is added and displayed

```mermaid

sequenceDiagram
    participant User
    participant Browser
    participant Server

    %% User initiates the process by clicking the form button
    User->>Browser: Clicks the button on the form

    %% Browser sends the form data to the server
    Browser->>Server: POST /new_note (form data)
    note over Browser: Sends form data to the server

    %% Server processes the request and stores the note
    Server->>Server: Process request and add note to array
    Server-->>Browser: HTTP 302 Redirect

    %% Browser requests the updated notes page
    Browser->>Server: GET /notes
    Server-->>Browser: HTML document

    %% Browser requests additional assets (CSS and JavaScript)
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: CSS file

    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>Browser: JavaScript file

    %% JavaScript fetches the updated notes from the server
    note right of Browser: JavaScript fetches notes from server
    Browser->>Server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: JSON file

    %% Browser renders the updated notes on the page
    note right of Browser: Browser renders notes
    note over Browser: Page reloads with the new note

    %% Updated notes page is displayed to the user
    Browser-->>User: Displays updated Notes page