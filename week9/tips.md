### persistent connections
In Http/1.0, the default connection is not persistent connection, while starting from Http/1.1, keep-alive is the default option.
Actually, the non-persistent and persistent connections of Http are esseantially different connections of the TCP layer.

However, a keep-alive connection won't last forever. most server kill inactive connections to prevent an immense amount of open connections. The response of a keep-alive may contains a timeout to inform the client how long the server will keep the connection open.