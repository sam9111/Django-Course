Sessions

All communication between the server and client is done with HTTP, which is a stateless protocol. stateless means that every request is an independednt transaction, each one does not affect the other, HTTP does not know what request came before it or how many times it was called, it has no state.

So how do website's keep track of you? if you have ever logged into anything anywhere, you know that you remain logged in for a certain period of time, you can close your browser, restart it and you will still be logged in. How does this work?

Django uses cookies to keep track of sessions, so what are cookies?

An HTTP cookie (web cookie, browser cookie) is a small piece of data that a server sends to a user's web browser. The browser may store the cookie and send it back to the same server with later requests.

When you visit a page that django renders, Django will create a new random key and send it over to your browser as a cookie, everytime you visit any route in the same server, the cookie is sent along with the request, when django sees the cookie it knows that its you sending the request and sets the context accordingly.

You can also store values in sessions, maybe a login time and a session timeout, maybe a language preference, anything like that. These values are stored in the session table and be accessed in the view.

Lets take a quick example to see how we can set and get values from the session.

-- Video