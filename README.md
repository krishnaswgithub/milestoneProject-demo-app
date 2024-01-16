# milestoneProject-demo-app

## Table of Contents
    1. Endpoints Documentation
        * Authentication
        * Blog Management

    2. User Flow with Postman
        * Step 1: User Registration
        * Step 2: User Login
        * Step 3: Add a Blog
        * Step 4: Fetch All Blogs
        * Step 5: Update a Blog
        * Step 6: Add a Comment
        * Step 7: Fetch a Comment
        * Step 8: Vote on a Blog

## Endpoints Documentation
### Authentication

    1. User Registration
        * Endpoint: POST /signup
        * Request Body:
            {
                "username": "example_username",
                "password": "example_password",
                "email": "user@example.com"
            }

        * Response:
        Success (HTTP 201):
            {
                "message": "User registered successfully",
                "token": "example_token"
            }

        Failure (HTTP 401):
            {
                "message": "User registering failed",
                "status": "error"
            }

    2. User Login
        Endpoint: POST /login
        Request Body:
            {
              "username": "example_username",
              "password": "example_password"
            }

        Response:
        Success (HTTP 201):
            {
              "message": "Login success",
              "token": "example_token"
            }

        Failure (HTTP 401):
            {
              "message": "Auth failed",
              "status": "error"
            }
        3. Get User Details
            Endpoint: POST /getuser
            Request Body:
                {
                    "id": "example_user_id"
                }

            Response:
            Success (HTTP 201):
                {
                  "user": {
                    "username": "example_username",
                    "email": "user@example.com",
                    "createdAt": "example_timestamp",
                    "updatedAt": "example_timestamp"
                  }
                }

            Failure (HTTP 401):
                {
                  "message": "Unauthorized access",
                  "status": "error"
                }

## Blog Management
    4. Fetch All Blogs
        Endpoint: GET /
        Response:
        Success (HTTP 201):
            {
              "blogs": [
                {
                  "title": "Example Blog",
                  "description": "Lorem Ipsum...",
                  "tag": ["tag1", "tag2"],
                  "imageUrl": "example_image_url",
                  "user": "example_user_id",
                  "username": "example_username",
                  "upvote": 0,
                  "downvote": 0,
                  "comments": [],
                  "createdAt": "example_timestamp",
                  "updatedAt": "example_timestamp"
                },
                // Additional blogs...
              ]
            }

        Failure (HTTP 500):
            {
              "message": "Internal Server Error"
            }

    5. Add a Blog
        Endpoint: POST /addblog
        Request Body:
            {
              "title": "Example Blog",
              "description": "Lorem Ipsum...",
              "tag": ["tag1", "tag2"],
              "imageUrl": "example_image_url"
            }

        Response:
        Success (HTTP 200):
            {
              "blog": {
                "title": "Example Blog",
                "description": "Lorem Ipsum...",
                "tag": ["tag1", "tag2"],
                "imageUrl": "example_image_url",
                "user": "example_user_id",
                "username": "example_username",
                "upvote": 0,
                "downvote": 0,
                "comments": [],
                "createdAt": "example_timestamp",
                "updatedAt": "example_timestamp"
              }
            }

        Failure (HTTP 500):
            {
              "message": "Internal Server Error"
            }

    6. Update a Blog
        Endpoint: PUT /update/:id
        Request Parameters:
        id: ID of the blog to be updated
        Request Body (Optional):
            {
              "title": "Updated Blog Title",
              "description": "Updated Blog Description",
              "tag": ["tag3", "tag4"],
              "imageUrl": "updated_image_url"
            }

        Response:
        Success (HTTP 200):
            {
              "status": "success",
              "blog": {
                // Updated blog details...
              }
            }

        Failure (HTTP 500):
            {
              "message": "Internal Server Error"
            }

    7. Delete a Blog
        Endpoint: DELETE /delete/:id
        Request Parameters:
        id: ID of the blog to be deleted
        Response:
        Success (HTTP 200):
            {
              "status": "success",
              "blog": {
                // Deleted blog details...
              }
            }

        Failure (HTTP 404 or 403):
            {
              "message": "Blog not found",
              "status": "error"
            }

    8. Add a Comment
        Endpoint: POST /addcomment/:id
        Request Parameters:
        id: ID of the blog to add a comment to
        Request Body:
            {
              "message": "Example Comment Message",
              "parentCommentId": "example_parent_comment_id"
            }

        Response:
        Success (HTTP 200):
            {
              "newComment": {
                "user": "example_user_id",
                "message": "Example Comment Message",
                "parentComment": "example_parent_comment_id",
                "blog": "example_blog_id",
                "like": 0,
                "isNested": true,
                "createdAt": "example_timestamp",
                "updatedAt": "example_timestamp"
              }
            }

        Failure (HTTP 500):
            {
              "message": "Internal Server Error"
            }

    9. Fetch a Comment
        Endpoint: GET /getcomment/:id
        Request Parameters:
        id: ID of the comment to be fetched
        Response:
        Success (HTTP 201):
            {
              "comment": {
                "user": "example_user_id",
                "message": "Example Comment Message",
                "parentComment": "example_parent_comment_id",
                "blog": "example_blog_id",
                "like": 0,
                "isNested": true,
                "createdAt": "example_timestamp",
                "updatedAt": "example_timestamp"
                }
            }

        Failure (HTTP 404):
            {
              "message": "Comment not found",
              "status": "error"
            }

    10. Vote on a Blog
        Endpoint: POST /vote/:id
        Request Parameters:
        id: ID of the blog to vote on
        Request Body:
            {
                "voteType": "upvote" // or "downvote"
            }

        Response:
        Success (HTTP 200):
            {
                "message": "Voted Successfully",
                "blog": {
                // Updated blog details...
                }
            }

        Failure (HTTP 404 or 400):
            {
                "message": "Blog not found or User has already voted",
                "status": "error"
            }

# User Flow with Postman

Step 1: User Registration

Step 2: User Login

Step 3: Add a Blog

Step 4: Fetch All Blogs

Step 5: Update a Blog

Step 6: Add a Comment

Step 7: Fetch a Comment

Step 8: Vote on a Blog
