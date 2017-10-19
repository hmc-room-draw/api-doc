# Backend endpoints

## Existing Routes

```
              Prefix Verb   URI Pattern                          Controller#Action
               pulls GET    /pulls(.:format)                     pulls#index
                     POST   /pulls(.:format)                     pulls#create
            new_pull GET    /pulls/new(.:format)                 pulls#new
           edit_pull GET    /pulls/:id/edit(.:format)            pulls#edit
                pull GET    /pulls/:id(.:format)                 pulls#show
                     PATCH  /pulls/:id(.:format)                 pulls#update
                     PUT    /pulls/:id(.:format)                 pulls#update
                     DELETE /pulls/:id(.:format)                 pulls#destroy
    room_assignments GET    /room_assignments(.:format)          room_assignments#index
                     POST   /room_assignments(.:format)          room_assignments#create
 new_room_assignment GET    /room_assignments/new(.:format)      room_assignments#new
edit_room_assignment GET    /room_assignments/:id/edit(.:format) room_assignments#edit
     room_assignment GET    /room_assignments/:id(.:format)      room_assignments#show
                     PATCH  /room_assignments/:id(.:format)      room_assignments#update
                     PUT    /room_assignments/:id(.:format)      room_assignments#update
                     DELETE /room_assignments/:id(.:format)      room_assignments#destroy
                     GET    /auth/:provider/callback(.:format)   sessions#create
        auth_failure GET    /auth/failure(.:format)              redirect(301, /)
              logout GET    /logout(.:format)                    sessions#destroy
            sessions POST   /sessions(.:format)                  sessions#create
             session DELETE /sessions/:id(.:format)              sessions#destroy
               login GET    /login(.:format)                     logins#show
               users GET    /users(.:format)                     users#index
                     POST   /users(.:format)                     users#create
            new_user GET    /users/new(.:format)                 users#new
           edit_user GET    /users/:id/edit(.:format)            users#edit
                user GET    /users/:id(.:format)                 users#show
                     PATCH  /users/:id(.:format)                 users#update
                     PUT    /users/:id(.:format)                 users#update
                     DELETE /users/:id(.:format)                 users#destroy
               dorms GET    /dorms(.:format)                     dorms#index
                     POST   /dorms(.:format)                     dorms#create
            new_dorm GET    /dorms/new(.:format)                 dorms#new
           edit_dorm GET    /dorms/:id/edit(.:format)            dorms#edit
                dorm GET    /dorms/:id(.:format)                 dorms#show
                     PATCH  /dorms/:id(.:format)                 dorms#update
                     PUT    /dorms/:id(.:format)                 dorms#update
                     DELETE /dorms/:id(.:format)                 dorms#destroy
               rooms GET    /rooms(.:format)                     rooms#index
                     POST   /rooms(.:format)                     rooms#create
            new_room GET    /rooms/new(.:format)                 rooms#new
           edit_room GET    /rooms/:id/edit(.:format)            rooms#edit
                room GET    /rooms/:id(.:format)                 rooms#show
                     PATCH  /rooms/:id(.:format)                 rooms#update
                     PUT    /rooms/:id(.:format)                 rooms#update
                     DELETE /rooms/:id(.:format)                 rooms#destroy
              suites GET    /suites(.:format)                    suites#index
                     POST   /suites(.:format)                    suites#create
           new_suite GET    /suites/new(.:format)                suites#new
          edit_suite GET    /suites/:id/edit(.:format)           suites#edit
               suite GET    /suites/:id(.:format)                suites#show
                     PATCH  /suites/:id(.:format)                suites#update
                     PUT    /suites/:id(.:format)                suites#update
                     DELETE /suites/:id(.:format)                suites#destroy
                root GET    /                                    login#show
```

## Notes

* All endpoints except `/login` redirect you to the login page if you're not
  logged in, and similarly to the form specified by `FORM_URL` in `.env` if you
  have not completed the form.
* `User` has full coverage for authorization and field validation checks but
  currently no other models do
* `Session` endpoints with the exception of `#destroy` are only to be called
  automatically by the Google OAuth callback.
* We will not be implementing our own forms, but instead using Google Forms,
  with verification done by checking the resulting spreadsheet

## To-do

- `/pulls/{suite_id}`

Puts the current user into a suite. TODO: How this data will be structured
is a bit unclear since I do not know all the possible ways to pull people in.

```
{
    room_number: "202D",
    roommates: [
        "1234567890"
    ],
    pulls: [
        // recursive structure?
    ]
}
```

- `GET /suites/{suite_id}`

Gets the list of rooms in the given suite as well as suite metadata

```
{
    restrictions: {
        permits_alcohol: false,
        only_gender: "male"
    },
    rooms: [
        <room IDs of some sort>
    ]
}
```
