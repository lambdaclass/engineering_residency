# Rust Project: Linkchecker

The goal of this project is to write a program that takes a text file as input containing a list of URLs in markdown format. 

The program must:
- parse the file, 
- extract the URLs, 

And for every URL, the program must: 
- query them to obtain the HTTP body, 
- if succesful:
  - parse the HTML
  - extract the `<title>` tag

- Finally, it must output a new markdown file with the URLs properly formatted as 
  - `[ EXTRACTED_TITLE ] ( URL )` if the request was succesful.
  - `[ HUMAN READABLE ERROR CODE ] ( URL )`

A strict requirement is that the URLs must be processed concurrently 32 at a time, i.e. don't wait for one request to finish before processing the next. 
You may use the `reqwest` crate to perform the HTTP requests. 

Remember to follow the [general guidelines](../README.md#learning-projects-guidelines) for projects!
