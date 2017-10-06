# Backend endpoints

## Admin

- `POST /admin/login`
- `POST /admin/logout`

- `GET /pulls`

Gets the pull history (JSON with a list of pulls, see below).

- `POST /pull/create`
- `POST /pull/update`
- `POST /pull/remove`

Create/update/remove a pull.

## Student

- `POST /student/signup`
- `POST /student/login`
- `POST /student/logout`

Exact JSON structure TBD. Google OAuth based.

- `GET /student/{id}`
- `GET /students`

Gets info for a student. Info returned may depend on permissions of current
user. For instance, if a pre-placed student has chosen to anonymize himself,
his room will not be present in the returned data.

```
{
    name: "Stu Dent",
    email: "student@hmc.edu",
    year: 1,                         // [0,1,2,3] = frosh,soph,junior,senior
    room_draw_num: 54,
}
```

## Form

`GET /form`

Gets the form, currently just a list of ordered questions.

```
{
  questions: {
    1: "What is the airspeed velocity of an unladen swallow?"
    2: ...
  }
}
```

`POST /form`

Posts a response to the form - answers in same order as questions.

```
{
    answers: [string]
}
```

`POST /form/question/create`
`POST /form/question/update/{id}`
`POST /form/question/delete/{id}`

Creates/updates/deletes a question on the form. Admin-only.


## Rooms

- `POST /suite/create`
- `POST /suite/update/{id}`
- `POST /suite/delete/{id}`

- `POST /room/create`
- `POST /room/update/{id}`
- `POST /room/delete/{id}`

- `GET /room/{dorm}/{room_number}`

Gets info for a room.

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

- `POST /pull/{suite_id}`

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

- `GET /suite/{suite_id}`

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
