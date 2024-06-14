# What is SQLAlchemy?

SQLAlchemy is a popular SQL toolkit and Object-Relational Mapping (ORM) library for Python. It provides a comprehensive set of tools for working with databases, making it easier to interact with relational databases using Python code.

### Why Use SQLAlchemy?

- **Abstraction**: Provides an abstraction layer that allows developers to work with databases using Python objects rather than raw SQL queries.
- **ORM**: Facilitates the mapping of Python classes to database tables, making it easier to perform CRUD (Create, Read, Update, Delete) operations.
- **Portability**: Makes your code more portable across different database systems.
- **Flexibility**: Offers flexibility to use raw SQL when needed while still benefiting from ORM features.
- **Productivity**: Simplifies database migrations and schema management.

---

## How to Use SQLAlchemy

### Installation

First, install SQLAlchemy using pip:

```
pip install sqlalchemy
```

### Basic Configuration

To use SQLAlchemy, you need to set up a connection to your database and define your ORM models.

```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker

# Define the SQLite database URL
DATABASE_URL = "sqlite:///example.db"

# Create an engine
engine = create_engine(DATABASE_URL)

# Define a base class
Base = declarative_base()

# Define a session
Session = sessionmaker(bind=engine)
session = Session()
```

### Define Models

Models are Python classes that represent database tables.

```python
class User(Base):
    __tablename__ = 'users'

    id = Column(Integer, primary_key=True)
    name = Column(String)
    email = Column(String)

    def __repr__(self):
        return f"<User(name={self.name}, email={self.email})>"
```

### Create Tables

Create the tables in the database based on the defined models.

```python
Base.metadata.create_all(engine)
```

### CRUD Operations

#### Create

```python
# Create a new user
new_user = User(name="John Doe", email="john.doe@example.com")
session.add(new_user)
session.commit()
```

#### Read

```python
# Read all users
users = session.query(User).all()
for user in users:
    print(user)
```

#### Update

```python
# Update a user
user = session.query(User).filter_by(name="John Doe").first()
user.email = "john.newemail@example.com"
session.commit()
```

#### Delete

```python
# Delete a user
user = session.query(User).filter_by(name="John Doe").first()
session.delete(user)
session.commit()
```

---

### Summary

Here's a summary table of the basic CRUD operations:

| Operation  | Code Example                                                     |
| ---------- | ---------------------------------------------------------------- |
| **Create** | `new_user = User(name="John Doe", email="john.doe@example.com")` |

`session.add(new_user)`  
`session.commit()` |
| **Read** | `users = session.query(User).all()`  
`for user in users: print(user)` |
| **Update** | `user = session.query(User).filter_by(name="John Doe").first()`  
`user.email = "john.newemail@example.com"`  
`session.commit()` |
| **Delete** | `user = session.query(User).filter_by(name="John Doe").first()`  
`session.delete(user)`  
`session.commit()` |

### Additional Resources

- [SQLAlchemy Documentation](https://docs.sqlalchemy.org/)
- [SQLAlchemy ORM Tutorial](https://docs.sqlalchemy.org/en/14/orm/tutorial.html)
- [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/) for integrating SQLAlchemy with Flask applications

Using SQLAlchemy can significantly simplify database interactions in your Python applications, making your code more maintainable and efficient.

---

## Feel free to reach out if you have any questions or need help getting started!

Github: [https://0xaungkon.github.io/](https://0xaungkon.github.io/)

Linkedin: [https://www.linkedin.com/in/aungkon-malakar/](https://www.linkedin.com/in/aungkon-malakar/)

Facebook: [https://www.facebook.com/0xAungkon/](https://www.facebook.com/0xAungkon/)

Email: [aungkonmalakar@gmail.com](mailto:aungkonmalakar@gmail.com)
