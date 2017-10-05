# Preliminary DB layout

To deal with…
* Privileges (student, admin, super-admin)
* Google OAuth support

```
Account --- TBD: try to use Google OAuth
  has_one: Student (nullable)

Student
  belongs_to: Account (nullable)
  belongs_to: Room (nullable)
* name: str
* email: str
* student_id: str
* year: int
* room_draw_num: int
* prev_room: (foreign key to Room)

Room
  belongs_to: Suite
  has_many: Student
* dorm: (foreign key to Dorm)
* floor: int
* suite: (foreign key to Suite)
* room_num: str
* capacity: int

Suite
  has_many: Room
* Description: string
* Restrictions (only male/female etc): TBD

Pull - TBD

Survey - TBD
```
