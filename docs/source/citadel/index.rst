.. Citadel documentation master file, created by
   sphinx-quickstart on Thu Oct  6 14:52:34 2022.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

Citadel Documentation
======================

The Citadel application is a tool for visualizing graphs through the web
browser. Users can explore their data collaboratively by uploading their datasets to the cloud and accessing the visualization through a web browser. By leveraging the 3D capabilities of the Microsoft Hololens 2,
users can view the graph in immersive 3D within their working environment.
Lastly, developers can interface with the Citadel API to engineer graph simulations which users can easily apply to a live visualization session.

The server and web client are written in Typescript using the Express and React frameworks.
The 3D visualization is written in C# using the Unity game engine.

.. * :ref:`genindex`
.. * :ref:`modindex`
.. * :ref:`search`


.. .. toctree::
..    :maxdepth: 3
..    :caption: Contents:

.. toctree::
    client
    server
    ar-unity
    api
    shared
