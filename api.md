# Backend endpoints

## Existing Routes

```
      Prefix Verb   URI Pattern                        Controller#Action
       users GET    /users(.:format)                   users#index
             POST   /users(.:format)                   users#create
    new_user GET    /users/new(.:format)               users#new
   edit_user GET    /users/:id/edit(.:format)          users#edit
        user GET    /users/:id(.:format)               users#show
             PATCH  /users/:id(.:format)               users#update
             PUT    /users/:id(.:format)               users#update
             DELETE /users/:id(.:format)               users#destroy
       dorms GET    /dorms(.:format)                   dorms#index
             POST   /dorms(.:format)                   dorms#create
    new_dorm GET    /dorms/new(.:format)               dorms#new
   edit_dorm GET    /dorms/:id/edit(.:format)          dorms#edit
        dorm GET    /dorms/:id(.:format)               dorms#show
             PATCH  /dorms/:id(.:format)               dorms#update
             PUT    /dorms/:id(.:format)               dorms#update
             DELETE /dorms/:id(.:format)               dorms#destroy
       rooms GET    /rooms(.:format)                   rooms#index
             POST   /rooms(.:format)                   rooms#create
    new_room GET    /rooms/new(.:format)               rooms#new
   edit_room GET    /rooms/:id/edit(.:format)          rooms#edit
        room GET    /rooms/:id(.:format)               rooms#show
             PATCH  /rooms/:id(.:format)               rooms#update
             PUT    /rooms/:id(.:format)               rooms#update
             DELETE /rooms/:id(.:format)               rooms#destroy
      suites GET    /suites(.:format)                  suites#index
             POST   /suites(.:format)                  suites#create
   new_suite GET    /suites/new(.:format)              suites#new
  edit_suite GET    /suites/:id/edit(.:format)         suites#edit
       suite GET    /suites/:id(.:format)              suites#show
             PATCH  /suites/:id(.:format)              suites#update
             PUT    /suites/:id(.:format)              suites#update
             DELETE /suites/:id(.:format)              suites#destroy
             GET    /auth/:provider/callback(.:format) sessions#create
auth_failure GET    /auth/failure(.:format)            redirect(301, /)
      logout GET    /logout(.:format)                  sessions#destroy
    sessions POST   /sessions(.:format)                sessions#create
     session DELETE /sessions/:id(.:format)            sessions#destroy
       login GET    /login(.:format)                   logins#show
             GET    /users(.:format)                   users#index
             POST   /users(.:format)                   users#create
             GET    /users/new(.:format)               users#new
             GET    /users/:id/edit(.:format)          users#edit
             GET    /users/:id(.:format)               users#show
             PATCH  /users/:id(.:format)               users#update
             PUT    /users/:id(.:format)               users#update
             DELETE /users/:id(.:format)               users#destroy
             GET    /rooms(.:format)                   rooms#index
             POST   /rooms(.:format)                   rooms#create
             GET    /rooms/new(.:format)               rooms#new
             GET    /rooms/:id/edit(.:format)          rooms#edit
             GET    /rooms/:id(.:format)               rooms#show
             PATCH  /rooms/:id(.:format)               rooms#update
             PUT    /rooms/:id(.:format)               rooms#update
             DELETE /rooms/:id(.:format)               rooms#destroy
             GET    /suites(.:format)                  suites#index
             POST   /suites(.:format)                  suites#create
             GET    /suites/new(.:format)              suites#new
             GET    /suites/:id/edit(.:format)         suites#edit
             GET    /suites/:id(.:format)              suites#show
             PATCH  /suites/:id(.:format)              suites#update
             PUT    /suites/:id(.:format)              suites#update
             DELETE /suites/:id(.:format)              suites#destroy
             GET    /dorms(.:format)                   dorms#index
             POST   /dorms(.:format)                   dorms#create
             GET    /dorms/new(.:format)               dorms#new
             GET    /dorms/:id/edit(.:format)          dorms#edit
             GET    /dorms/:id(.:format)               dorms#show
             PATCH  /dorms/:id(.:format)               dorms#update
             PUT    /dorms/:id(.:format)               dorms#update
             DELETE /dorms/:id(.:format)               dorms#destroy
        root GET    /                                  login#show
```

## To-do

`/forms/`

Gets the form, currently just a list of ordered questions.

```
{
  questions: {
    1: "What is the airspeed velocity of an unladen swallow?"
    2: ...
  }
}
```

`/form/questions/`

Creates/updates/deletes a question on the form. Admin-only.


- `GET /rooms/{dorm}/{room_number}`

Gets info for a room. Right now /rooms/{id} can get rooms, but it would be nice
if we could use this kind of endpoint to get rooms as well.

```
{
    dorm: "Sontag"
    floor: 2
    room_num: "202D",
    suite: (suite ID),
    capacity: 2,
    students: [
        "1234567890",
        "1234567890"
    ]
}
```

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
