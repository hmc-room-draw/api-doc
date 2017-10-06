# Preliminary DB layout

Accounts support Google OAuth login.
```
Account
  provider
  uid
  oauth_token
  oauth_expires_at:datetime
  email

  has_one: Student (nullable)
  has_one: Admin (nullable)
```

```
Student
  email: str
  name: str
  class: int
  room_draw_num: int

  belongs_to: Account (nullable)
  belongs_to: Room (nullable)
```

```
Admin
  email: str
  -- Some things related to roles/permissions; TODO: how to do this?

  belongs_to: Account
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
  room_num: str
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
