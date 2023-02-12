### Authentication is never sent to the destination server.

`Authorization`, `Cookie`, and `Proxy-Authorization` headers are not sent to the
server. Avoid including user info in parts of imported URLs. A security model
for safely using these on the server is being worked on.
