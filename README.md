# Networks and Systems, Networks Coursework

This coursework was to implement a client-server system, which implements a simple anonymous bulletin board system using TCP.

## Server Program

- Once the server starts, it listens on a specified IP and port for incoming TCP/IP requests
- The server receives requests from clients and responds to them as described below
- The server retrieves any requested information and returns the result to the client
- The server must be able to handle the following errors
  - Unavailable/busy port: print error and exit
  - No messaged boards defined: print error and exit
  - Specified board does not exist: notify client of error
  - Invalid message: notify client of error

## Server message board state

- The server maintains that the message board state using the contents of the "board" subfolder of the working directory it was executed in
- Before running your server program, the user will create the "board" folder, and one or more empty subfolders inside "board" folder to represent message boards
- To post a message, the server creates a file with the appropriate name in the corresponding folder
- To list message boards or read messages, the server examines the contents of the "board" folder in the file system

## Client program

- The client sends its requests to a server listening on a specified host and port
- When the client starts, it should immediately attempt to connect to the server and send a `GET_BOARDS` command to find out what message boards exist, and display the result to the user as a numbered list
- The client then waits for user input, which must be one of

  - Any number from the list - requests a list of 100 most recent messages in that board from the server, and displays the contents of these messages
  - `POST` - posts a message, by first prompting the user for:

    1. The number of the board to post to
    2. The message title
    3. The message content

    Then sending a `POST_MESSAGE` message to the server

  - `QUIT` - Closes any open connections and terminates the client

- After sending a command to the server, the client must inform the user that the command was successful, or if not should display an appropriate error message
- Your code should handle situations that may occur prior, during and after client server interaction

## Log Files

The server program should record information for each request it receives during all client-server communication
