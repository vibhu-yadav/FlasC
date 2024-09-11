# Flasc

Flasc is a C library designed to create simple concurrent RESTful web servers, primarily suited for educational or basic use cases. It is not intended for high-performance scenarios. This library aims to facilitate the creation of a backend in C with minimal complexity.

**Key Features:**
- HTTP 1.1 compatible request parsing
- RESTful interface
- Endpoint handler creation
- Endpoint template rendering
- Custom dictionary module for data processing
- Support for form data, query parameters, and JSON parsing
- HTTP 1.1 compliance
- Various threading models
- Cookie-based authentication
- CORS and CSRF support

## Contents
* [Overview](#overview)
* [Prerequisites](#prerequisites)
* [Running the Application](#running-the-application)
* [Getting Started](#getting-started)
* [Structure Definitions](#structure-definitions)
* [Webserver Setup and Usage](#webserver-setup-and-usage)
* [Request Parsing](#request-parsing)
* [Response Building](#response-building)
* [Authentication](#authentication)
* [Additional Examples](#additional-examples)

## Overview
Flasc is designed to provide an accessible way to build university-level HTTP servers using REST principles in C. The objective of this library is to handle various HTTP features with a straightforward interface, allowing developers to focus on their application logic rather than HTTP intricacies. With Flasc, you can join the ranks of those who have developed RESTful HTTP servers in C, but with much less effort!

Flasc can decode certain body formats and automatically convert them into a custom dictionary format. This applies to query parameters and the bodies of *POST* and *PUT* requests when the *application/x-www-form-urlencoded* header is used.

[Back to Contents](#contents)

## Prerequisites
To be announced

## Running the Application
Create a file named `main.c` and include the header file with `#include "Flasc.h"`. Define your endpoints according to the instructions. Then:
1. Execute `make` to compile and generate the executable file `server`.
2. Run the executable with the port number as an argument: `./server 8080`.

## Getting Started
Here's a basic example demonstrating how to set up a server and handle requests for the path `/hello`:

```cpp
    #include <stdio.h>
    #include "flasc.h"

    char* hello(Request *req, int new_socket)
    {
        return "Hello, This is Flasc!";
    }

    int main(int argc, char *argv[])
    {
        char *methods[] = {"GET", "POST"};
        int num = 2;
        add_route("/hello", &hello, methods, num);
        create_app(port);

        return 0;
    }
```

To test this example, use the following curl command:

    curl -XGET -v http://localhost:8080/hello

In this code, `add_route` registers the endpoint with the allowed methods. It takes the route path, a function pointer to the handler, an array of allowed methods, and the array's length. Each handler function receives a `Request` struct and the client socket descriptor. In this example, the handler returns a string literal, which will be visible on the client side.

[Back to Contents](#contents)
