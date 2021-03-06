# CodeBud Internal API Docs


JWT not enabled at the moment
<!-- All routes are protected by jwt which can be obtained from /user/login or /admin/login
User jwt gives access to /user/* and /meetup/* endpoints
Admin jwt gives access to /admin/* endpoints -->


# User

## - /user/signUp
    POST
        Send : 
            - username as req.body.username
            - password as req.body.password
            - email as req.body.email
            - firstName as req.body.firstName
            - lastName as req.body.lastName
            - title as req.body.title
            - skills as req.body.skills (csv)
            - city as req.body.city
            - state as req.body.state

        Receive : 
            Confirmation for saved user      

## - /user/login
    POST
        Send :
            - username as req.body.username
            - password as req.body.password

        Receive : 
            Login success message and JWT

## - /user/listFriends
    GET
        Send :
            - username as req.body.username

        Receive : 
            List of friends of user

## - /user/listRequestsReceived
    GET
        Send :
            - username as req.body.username

        Receive : 
            List of friend requests received by user

## - /user/listRequestsSent
    GET
        Send :
            - username as req.body.username

        Receive : 
            List of friend requests sent by user

## - /user/addFriend
    POST
        Send :
            - username as req.body.username
            - addUsername as req.body.addUsername

        Receive : 
            Confirmation for friend request sent

## - /user/respondRequest
    POST
        Send :
            - username as req.body.username
            - addUsername as req.body.addUsername
            - response as req.body.response

        Receive : 
            Confirmation for response to request

## - /user/removeFriend
    POST
        Send :
            - username as req.body.username
            - removeUsername as req.body.removeUsername

        Receive : 
            Confirmation for friend removed

## - /user/blockUser
    POST
        Send :
            - username as req.body.username
            - blockUsername as req.body.blockUsername

        Receive : 
            Confirmation for user blocked


# Meetup

## - /meetup/create
    POST
        Send : 
            - username as req.body.username
            - title as req.body.title
            - description as req.body.description
            - invited as req.body.invited (comma separated string)
            - street as req.body.street
            - city as req.body.city
            - state as req.body.state
            - datetime as req.body.datetime
            - duration as req.body.duration

        Receive : 
            Confirmation for meetup created

## - /meetup/listByUsername
    GET
        Send :
            - username as req.body.username

        Receive :
            List of meetups created by user

## - /meetup/listByLocation
    GET
        Send :
            - city as req.body.city
            - state as req.body.state
        
        Receive :
            List of meetups in city selected

## - /meetup/listByInvitation
    GET
        Send :
            - username as req.body.username

        Receive :
            List of meetups invited to

## - /meetup/inviteUsers
    POST
        Send :
            - username as req.body.username
            - meetupId as req.body.meetupId
            - invitees as req.body.invitees (comma separated string)

        Receive :
            Confirmation of users invited

## - /meetup/respondInvitation
    POST
        Send :
            - username as req.body.username
            - meetupId as req.body.meetupId
            - response as req.body.response (Yes/No/Maybe)

        Receive :
            Confirmation of response to invitation

## - /meetup/listRequested
    POST
        Send :
            - username as req.body.username
            - meetupId as req.body.meetupId

        Receive :
            List of users requested to join

## - /meetup/requestJoin
    POST
        Send :
            - username as req.body.username
            - meetupId as req.body.meetupId

        Receive :
            Confirmation of request to join meetup

## - /meetup/respondRequest
    POST
        Send :
            - username as req.body.username
            - meetupId as req.body.meetupId
            - invitee as req.body.invitee
            - response as req.body.response (Yes/No)

        Receive :
            Confirmation of response to request

# Group

# ToDo

### - Add images to profile
### - Edit user profile
### - Delete/Edit Meetup
### - Socket for messaging
### - Search for users by skills, title and distance
### - Setup groups, create, add, delete