
<a href="#top" class="back-to-top">⬆️</a>

<style>
.back-to-top {
    position: fixed;
    bottom: 20px;
    right: 20px;
    background: #0078d4;
    color: white;
    padding: 12px 16px;
    border-radius: 50%;
    text-decoration: none;
    font-size: 22px;
    box-shadow: 0 4px 8px rgba(0,0,0,0.3);
    transition: opacity 0.3s ease-in-out;
    opacity: 0.8;
}
.back-to-top:hover {
    opacity: 1;
}
</style>


---
title: "Page d'exemple"
---

# Bienvenue

Ceci est une page d'exemple générée à partir de Markdown.
Desktop Sessions
A desktop session is a user-related execution context on 4D Server or 4D single-user that does not result from any web or REST access.

Just like in a web user session, the code executed in a desktop session has access to a Session object which provides functions and properties allowing you to store session values and to share them between user processes, for example using the session.storage object.

However, unlike the code executed in web user sessions, the code executed in desktop sessions is not controlled by roles and privileges. It can access any parts of the 4D application, including ORDA and data model classes. On 4D Server, users and groups feature can manage user accesses.

You can nevertheless share a desktop session with a web session so that a desktop user can access your 4D application through a web interface, using for example Qodly pages and Web areas.

Session types
Desktop sessions include:

Remote user sessions: In client/server applications, the session that manages the user processes on the server.
Stored procedures sessions: In client/server applications, the unique virtual user session that manages all stored procedures executed on the server.
Standalone sessions: Local session object returned in single-user application (useful in development and test phases of client/server applications).
note
Keep in mind that Web sessions are used as soon as the 4D project is accessed through web or REST requests and scalable sessions are enabled.

The following diagram shows the different session types and how they interact:



Remote user sessions
On the server, in "user processes" (i.e. processes related to remote users), the Session command returns a session object describing the current user session. This object is handled through the functions and properties of the Session class.

note
On a remote 4D, the Session command always returns null.

Related blog posts
4D remote session object with Client/Server connection and Stored procedure.

Usage
The session object allows you to handle information and privileges for the remote user session.

You can share data between all processes of the user session using the session.storage shared object. For example, you can launch a user authentication and verification procedure when a client connects to the server, involving entering a code sent by e-mail or SMS into the application. You then add the user information to the session storage, enabling the server to identify the user. This way, the 4D server can access user information for all client processes, enabling customized code to be written according to the user's role.

You can also assign privileges to a remote user session to control access when the session comes from Qodly pages running in web areas.

Availability
The remote user session object is available from:

Project methods that have the Execute on Server attribute (they are executed in the "twinned" process of the client process),
Triggers,
ORDA data model functions (except those declared with the local keyword),
Database methods such as On Server Open Connection and On Server Close Connection.
Stored procedure sessions
On the server, all stored procedures share the same virtual user session.

Usage
You can share data between all processes of a stored procedure session using the session.storage shared object.

Availability
The session object of stored procedures is available from:
