# Backend endpoints

## Students

- `POST /student/signup`

Submits a JSON object containing _account_ info (password, etc), which is used
to create an `Account` entry that is associated with a preexisting `Student`
entry.

Must be HTTPS-only.

```
{
    email: "student@hmc.edu",
    password: "12345",
    student_id: "1234567890"
}
```

- `POST /student/login`

Login. Must be HTTPS-only.

```
{
    email: "student@hmc.edu",
    password: "12345"
}
```

- `POST /student/logout`

Logout. Takes no params; current user is implied.

- `GET /student/{id}`

Gets info for a student. Info returned may depend on permissions of current
user. For instance, if a pre-placed student has chosen to anonymize himself,
his room will not be present in the returned data.

```
{
    name: "Stu Dent",
    email: "student@hmc.edu",
    student_id: "1234567890",
    year: 2020,
    room_draw_num: 54,
    prev_room: <room ID of some sort>
```

- `POST /student/preferences`

TODO for later. Allow students to update their preferences, e.g. anonymity,
male/female only suite, alcohol-free suite etc. This will be used later to
restrict entry into certain suites.

## Rooms

- `GET /room/{dorm}/{room_number}`

Gets info for a room.

```
{
    dorm: "Sontag"
    floor: 2
    room_num: "202D",
    suite: <suite ID of some sort>,
    capacity: 2,
    students: [
        "1234567890",
        "1234567890"
    ]
}
```

- `POST /room/{dorm}/{room_number}`

Puts the current user into a room.

- `POST /room/{dorm}/{room_number}/{student_id}`

Puts a student into a room. Will email anyone who is bumped out as a result.

```
{
    students: [
        "1234567890"
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
