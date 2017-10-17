# Preliminary DB layout

Accounts support Google OAuth login.
```
User
  last_name: str
  first_name: str
  email: str
  is_ashmc_admin: false
  is_super_admin: false

  oauth_token: str
  oauth_expires_at:datetime

  has_one: Student (nullable)
```

```
Student
  class: int
  room_draw_number: int
  has_participated: false

  belongs_to: User
  has_one: Room (nullable)
```

```
Dorm
  -- TBD. Will need to store regulations.
```

```
Suite
  -- TBD. Will need to store regulations.

  belongs_to: Dorm
  has_many: Room
```

```
Room
  dorm: (Dorm id)
  suite: (Suite id)
  floor: int
  number: str
  capacity: int

  belongs_to: Suite
  has_many: Student
```

```
SurveyQuestion
  id: int
  question: string
```

```
SurveyResponse
  answer: string

  belongs_to: SurveyQuestion
```

```
Pull
  suite: (Suite id)
  room: (Room id)
  timestamp: datetime

  belongs_to: Student
```

```
Session
    start: datetime
    end: datetime
    class: int          -- Freshman, sophomore, etc.
                        -- TODO: figure out senior rounds later...
```
