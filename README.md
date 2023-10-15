# simple-chatroom

A chatroom to allow interactions.

## Design Overview:
Redis:
   - Used to store messages and users.
   - Structure: 
     - users: `<username>`: Hash to store user's info like IP address and tripcode hash.
     - `messages`: List to store messages.
     - message: `<id>`: Hash to store individual message details
Reitit:
     - Handle routing for our application.
HTMX:
     - Client-side library to allow parts of the web page to be updated via AJAX, combined with websockets for real-time updates.

## Backend Components
### User management(login/logout)
- User submits username and optional tripcode for login.
- Backend hashes the tripcode if provided and stores it.
- IP address is also stored with the user's data in the session.
- Session is cleared during log out
### Message Management (add/edit/delete)
- User submits a message.
- Message, along with username and tripcode (or IP if no tripcode), is stored in Redis.
- When editing, backend checks tripcode(or IP) before allowing the action
- When deleting, backend checks tripcode(or IP) before allowing the action
### WebSocket Management
- This will handle real-time updates, messages are also sent over a WebSocket connection. (http-kit)




## License

Copyright © 2023 FIXME

This program and the accompanying materials are made available under the
terms of the Eclipse Public License 2.0 which is available at
http://www.eclipse.org/legal/epl-2.0.

This Source Code may also be made available under the following Secondary
Licenses when the conditions for such availability set forth in the Eclipse
Public License, v. 2.0 are satisfied: GNU General Public License as published by
the Free Software Foundation, either version 2 of the License, or (at your
option) any later version, with the GNU Classpath Exception which is available
at https://www.gnu.org/software/classpath/license.html.
