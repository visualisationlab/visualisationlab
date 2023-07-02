Overview
########


The Citadel application is a tool for visualizing graphs through the web
browser. Users can explore their data collaboratively by uploading their datasets to the cloud and accessing the visualization through a web browser. By leveraging the 3D capabilities of the Microsoft Hololens 2,
users can view the graph in immersive 3D within their working environment.
Lastly, developers can interface with the Citadel API to engineer graph simulations which users can easily apply to a live visualization session.

The server and web client are written in Typescript using the Express and React frameworks.
The 3D visualization is written in C# using the Unity game engine. This documentation is designed to help developers understand the architecture of the Citadel application and how to extend it.

Citadel uses a client/server architecture.

Server
======

Each client connects to a Citadel server. The server is responsible for:

- Managing user sessions
- Creating sessions from uploaded datasets
- Managing user connnections to sessions
- Managing dataset changes based on client input
- Deleting sessions
- Managing communication between a client and connected simulators
- Managing communication between a client and the 3D visualization

Each session has its own dataset and data history. Multiple users can connect to the same session. The server is responsible for managing the state of the session and communicating changes to all connected clients.

Client
======

The client is a web application that allows users to connect to a Citadel server session and visualize the graph. The client is responsible for:

- Requesting a new session from the server
- Connecting to a Citadel server session
- Displaying the graph visualization
- Changing the graph visualization based on user input
- Sending requests to the server when the user changes the underlying dataset

AR Visualisation
================

The AR visualisation is a Unity application that runs on the Microsoft Hololens 2. The AR visualisation is responsible for:

- Connecting to a Citadel server session through a client API endpoint
- Displaying the graph visualization in 3D
- Responding to connected client viewport changes
- Offering data inspection tools to the user

The AR visualisation is designed to be a passive viewer of the graph. It does not send requests to the server to change the underlying dataset.

API
===

The Citadel server exposes an API for clients to connect to. This connection runs through the server and is used to communicate changes to the underlying dataset.
