## 0.4: New note diagram

### Requirement

Create a diagram depicting the situation where the user creates a new note on the page https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field and clicking the Save button.

If necessary, show operations on the browser or on the server as comments on the diagram.

The diagram does not have to be a sequence diagram. Any sensible way of presenting the events is fine.

### Solution

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types a new note in the input field

    browser->>browser: User clicks "Save" button

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note { "content": "New note", "date": "2019-05-25T15:15:59.905Z" }
    activate server
    server-->>browser: 302 Found (URL Redirect). Form data: is sent with HTTP POST. Location: /notes
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Server asks browser for new GET request to /notes and fetches the updated notes list
    deactivate server

    Note right of browser: The browser updates the UI by displaying the new note
```
