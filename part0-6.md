New Note on Single Page Application Diagram

```mermaid
sequenceDiagram

    participant User

    participant Browser

    participant Server


    User->>Browser: Hace clic en el botón del formulario

    Browser->>Server: Enviar solicitud HTTP a https://studies.cs.helsinki.fi/exampleapp/spa

    note over Browser: La solicitud incluye los datos del formulario en el cuerpo

    Server->>Server: Procesar solicitud y agregar la nota al arreglo

    Server-->>Browser: XHR document {"message":"note created"}


    Note right of Browser: The browser executes the callback function that renders the notes

    note over Browser: The page reloads with the new note

    Browser-->>User: Displays the updated Notes page



