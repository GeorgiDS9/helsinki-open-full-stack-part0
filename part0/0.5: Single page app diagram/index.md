```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: SPA loads only one HTML document at the start; navigation is handled via JavaScript.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document (shell), separate JavaScript and CSS files loaded
    deactivate server

    Note right of browser: JavaScript is loaded once and persists, dynamically updating the DOM.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: CSS is loaded once and persists

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    Note right of browser: Data is fetched dynamically without reloading pages.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

     Note right of browser: User navigates using JavaScript, without triggering full page loads.
```
