# What is SQLAlchemy:

SQLAlchemy is a comprehensive SQL toolkit and Object-Relational Mapping (ORM) library for Python. It provides a full suite of well-known enterprise-level persistence patterns, designed for efficient and high-performing database access. SQLAlchemy provides a powerful and flexible way to interact with your database in Python applications.

---

### Why Use SQLAlchemy with FastAPI?

FastAPI is a modern, fast (high-performance) web framework for building APIs with Python 3.7+ based on standard Python type hints. Integrating SQLAlchemy with FastAPI allows developers to build APIs that efficiently interact with relational databases, leveraging SQLAlchemy's ORM capabilities to manage database interactions cleanly and effectively.

### Key Points of SQLAlchemy

1.  **ORM and Core**: SQLAlchemy has two primary components:
    - **Core**: Provides SQL expression language and a dialect system for DBAPI.
    - **ORM**: Builds on top of the Core and allows you to map Python classes to database tables.
2.  **Schema Definition**: Define your database schema using Python classes.
3.  **Query Building**: Construct SQL queries in a programmatic way, avoiding the need to write raw SQL.
4.  **Session Management**: Manages transactions and connections efficiently.
5.  **Database Agnostic**: Works with various database backends (e.g., SQLite, PostgreSQL, MySQL).

---

### Example: Using SQLAlchemy with FastAPI

Let's go through an example to demonstrate how to create, read, update, and delete records using SQLAlchemy within a FastAPI application.

### Step 1: Install Dependencies

First, you need to install FastAPI, SQLAlchemy, and an ASGI server (like Uvicorn):

```
pip install fastapi sqlalchemy uvicorn
pip install asyncpg  # If you are using PostgreSQL
```

### Step 2: Setting Up the Database and Models

```python
from fastapi import FastAPI, Depends, HTTPException
from sqlalchemy import Column, Integer, String, create_engine
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy.orm import sessionmaker, Session

DATABASE_URL = "sqlite:///./test.db"  # Replace with your database URL

engine = create_engine(DATABASE_URL, connect_args={"check_same_thread": False})
SessionLocal = sessionmaker(autocommit=False, autoflush=False, bind=engine)

Base = declarative_base()

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True, index=True)
    name = Column(String, index=True)
    email = Column(String, unique=True, index=True)

Base.metadata.create_all(bind=engine)

app = FastAPI()

# Dependency to get the session
def get_db():
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()
```

### Step 3: CRUD Operations

### Create a User

```python
from pydantic import BaseModel

class UserCreate(BaseModel):
    name: str
    email: str

@app.post("/users/", response_model=UserCreate)
def create_user(user: UserCreate, db: Session = Depends(get_db)):
    db_user = User(name=user.name, email=user.email)
    db.add(db_user)
    db.commit()
    db.refresh(db_user)
    return db_user
```

### Read Users

```python
from typing import List

class UserRead(BaseModel):
    id: int
    name: str
    email: str

    class Config:
        orm_mode = True

@app.get("/users/", response_model=List[UserRead])
def read_users(skip: int = 0, limit: int = 10, db: Session = Depends(get_db)):
    users = db.query(User).offset(skip).limit(limit).all()
    return users
```

### Update a User

```python
class UserUpdate(BaseModel):
    name: str
    email: str

@app.put("/users/{user_id}", response_model=UserRead)
def update_user(user_id: int, user: UserUpdate, db: Session = Depends(get_db)):
    db_user = db.query(User).filter(User.id == user_id).first()
    if db_user is None:
        raise HTTPException(status_code=404, detail="User not found")
    db_user.name = user.name
    db_user.email = user.email
    db.commit()
    db.refresh(db_user)
    return db_user
```

### Delete a User

```python
@app.delete("/users/{user_id}", response_model=UserRead)
def delete_user(user_id: int, db: Session = Depends(get_db)):
    db_user = db.query(User).filter(User.id == user_id).first()
    if db_user is None:
        raise HTTPException(status_code=404, detail="User not found")
    db.delete(db_user)
    db.commit()
    return db_user
```

---

### Summary

- **SQLAlchemy**: A powerful toolkit and ORM for Python, making it easier to work with databases.
- **FastAPI**: A modern web framework that makes it easy to build APIs quickly and efficiently.
- **Integration**: Using SQLAlchemy with FastAPI allows for efficient and structured database interactions.
- **CRUD Operations**: Demonstrated how to create, read, update, and delete database records with SQLAlchemy in a FastAPI application.

By following these steps, you can effectively integrate SQLAlchemy with FastAPI to manage your database operations in a clean and efficient manner.

---

## Feel free to reach out if you have any questions or need help getting started!

Github: [https://0xaungkon.github.io/](https://0xaungkon.github.io/)

Linkedin: [https://www.linkedin.com/in/aungkon-malakar/](https://www.linkedin.com/in/aungkon-malakar/)

Facebook: [https://www.facebook.com/0xAungkon/](https://www.facebook.com/0xAungkon/)

Email: [aungkonmalakar@gmail.com](mailto:aungkonmalakar@gmail.com)
