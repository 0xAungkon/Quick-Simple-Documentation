# What is Tortoise ORM?

Tortoise ORM is an easy-to-use Object Relational Mapper (ORM) for Python, inspired by Django. It is designed to be simple yet powerful, providing a high-level API for interacting with databases.

---

### Benefits of Tortoise ORM:

- **Asynchronous Support:** Fully asynchronous, making it ideal for modern async frameworks like FastAPI and Sanic.
- **Easy to Use:** Intuitive and simple to set up, with a syntax similar to Django's ORM.
- **Lightweight:** Minimalist with a small footprint, focusing on essential features.
- **Type Hinting:** Provides excellent support for type hinting and static analysis.
- **Flexible:** Supports multiple databases including SQLite, PostgreSQL, and MySQL.

---

### Comparison with SQLAlchemy and Other ORMs

| Feature       | Tortoise ORM                     | SQLAlchemy                          | Other ORMs                             |
| ------------- | -------------------------------- | ----------------------------------- | -------------------------------------- |
| Asynchronous  | Yes                              | Yes (with SQLAlchemy 1.4)           | Varies                                 |
| Ease of Use   | High (Django-like syntax)        | Medium (More complex and flexible)  | Varies (often simpler or more complex) |
| Type Hinting  | Excellent                        | Good                                | Varies                                 |
| Performance   | Good                             | Excellent (highly optimized)        | Varies                                 |
| Flexibility   | Moderate (focuses on simplicity) | High (very flexible and extensible) | Varies                                 |
| Documentation | Good                             | Excellent                           | Varies                                 |

---

### How to Use Tortoise ORM

### Installation

```
pip install tortoise-orm
```

### Basic Setup

1.  **Initialize Tortoise ORM**

```python
from tortoise import Tortoise, fields
from tortoise.models import Model

async def init():
    await Tortoise.init(
        db_url='sqlite://db.sqlite3',
        modules={'models': ['__main__']}
    )
    await Tortoise.generate_schemas()

class User(Model):
    id = fields.IntField(pk=True)
    username = fields.CharField(max_length=50)
    email = fields.CharField(max_length=100)

    def __str__(self):
        return self.username

import asyncio
asyncio.run(init())
```

### Example CRUD Operations

### Create

```python
from models import User

async def create_user(username: str, email: str):
    user = await User.create(username=username, email=email)
    return user

asyncio.run(create_user("john_doe", "john@example.com"))
```

### Read

```python
async def get_user(user_id: int):
    user = await User.get(id=user_id)
    return user

user = asyncio.run(get_user(1))
print(user)
```

### Update

```python
async def update_user(user_id: int, new_email: str):
    user = await User.get(id=user_id)
    user.email = new_email
    await user.save()

asyncio.run(update_user(1, "john_new@example.com"))
```

### Delete

```python
async def delete_user(user_id: int):
    user = await User.get(id=user_id)
    await user.delete()

asyncio.run(delete_user(1))
```

---

### Conclusion

Tortoise ORM is a robust choice for projects requiring an async ORM with straightforward and intuitive usage. While it may not have all the advanced features of SQLAlchemy, its simplicity and async capabilities make it a strong contender for modern Python web applications.

---

## Feel free to reach out if you have any questions or need help getting started!

Github: [https://0xaungkon.github.io/](https://0xaungkon.github.io/)

Linkedin: [https://www.linkedin.com/in/aungkon-malakar/](https://www.linkedin.com/in/aungkon-malakar/)

Facebook: [https://www.facebook.com/0xAungkon/](https://www.facebook.com/0xAungkon/)

Email: [aungkonmalakar@gmail.com](mailto:aungkonmalakar@gmail.com)
