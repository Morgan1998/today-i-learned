# Alright, what's a Use Case?

It's a single, complete goal that a real user or client application wants to achieve from start to finish. It represents the 'what' the user is trying to do, rather that the technical details of how the database handles it. For example: 'Place an Order', 'Reset Password', and 'Deactivate Account'.

# Some notes

1. It's all about the user and what they want done.
2. It dictates exactly the steps your service layer needs to coordinate to make that wish come true.
3. A single use case on the frontend usually maps directly to a single endpoint on the backend controller, keeping the API simple instead of those chatting APIs I mentioned above.
