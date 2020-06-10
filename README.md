# serpentine
serpentine is a Windows RAT (Remote Administration Tool) that lets your interact with the clients using a multiplatform RESTful server.

Functionalities:

- Startup

- Get files

- Put files

- Keylogger

- Reverse shell (Using `netcat` as a client, listen on a port `nc -l -p 5555` and request a reverse shell connection to that port)

- Reverse proxy (Using [`revp`](https://github.com/jafarlihi/revp), upload `revp` to the client and execute it with reverse shell)

### Dissection
`client` directory holds the Windows portion of the RAT made with C++ and Boost.

`server` holds the RESTful server portion made with Java and Spring.

`frontend` can hold any number of frontends that consume the RESTful API but currently holds only a terminal client made with Go.

#### API
`/client` GET --> Returns list of currently connected clients (clients that pinged in the last 10 seconds)

`/client` POST --> Changes name associated with a client

`/file/{client}` POST --> Fetches a file from a client

`/file/{client}` PUT --> Uploads a file to a client

`/shell/{client}` POST --> Makes a client initiate a reverse shell connection
