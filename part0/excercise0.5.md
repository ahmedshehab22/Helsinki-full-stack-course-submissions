Sequence Diagram
  the client clicked on the link ("https://studies.cs.helsinki.fi/exampleapp/spa")
  
  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    // the browser sent a request to the server get the web page " /notes " 
    
  activate server
  
  server-->>browser: HTML document
    // the server sent back a response containing the html document to the browser
    
  deactivate server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    // the browser read the link tag which contains link to the styling sheer ("main.css") so it sent a request to the server to get that file
    
  activate server
  
  server-->>browser: the css file
    // the server sent back a response containing the css document to the browser
    
  deactivate server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
      // the browser read the script tag which contains src to the js file ("main.js") so it sent a request to the server to get that file
  
  activate server
  
  server-->>browser: the JavaScript file
      // the server sent back a response containing the js file to the browser
  
  deactivate server

  *The browser starts executing the JavaScript code that fetches the JSON from the server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
        // the browser read executes the js file  which requests data ("data.json") so it sent a request to the server to get that file
  
  activate server
  
  server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    // the server sent back a response containing the json file to the browser
  
  deactivate server
  * after the data was sent successfully the event triggered and the js will append the data to the html document using DOM apis
