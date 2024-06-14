## Loguru in Python

### What is Loguru?

**Loguru** is a library in Python designed to simplify logging. It aims to make logging (the process of recording messages during the execution of a program) more intuitive and flexible compared to Python's built-in logging module.

### When Was It Created and Who Created It?

- **Creation Date**: Loguru was created and released in 2018.
- **Creator**: The library was developed by Delgan (a pseudonym for an individual developer who maintains the project).

### Purpose of Loguru

Loguru was created to address several limitations and complexities of Python's built-in logging module. Its primary goals include:

- Providing an easier setup with minimal boilerplate code.
- Offering more intuitive syntax for common logging tasks.
- Enhancing the flexibility and configurability of logging outputs.

### Alternatives to Loguru

There are several alternatives to Loguru for logging in Python. Here is a comparison table highlighting some of the key differences:

| Feature                  | Loguru    | Python Logging | Logbook        | Structlog      |
| ------------------------ | --------- | -------------- | -------------- | -------------- |
| Ease of Setup            | Very Easy | Moderate       | Moderate       | Moderate       |
| Async Support            | Yes       | Yes            | Yes            | Yes            |
| Custom Handlers          | Yes       | Yes            | Yes            | Yes            |
| Structured Logging       | Limited   | Limited        | Limited        | Excellent      |
| Rotating File Handler    | Built-in  | Requires Setup | Requires Setup | Requires Setup |
| Third-party Integrations | Limited   | Extensive      | Moderate       | Extensive      |

### Why Use Loguru?

- **Ease of Use**: Minimal configuration required to get started.
- **Flexibility**: Highly configurable logging handlers and outputs.
- **Intuitive Syntax**: Cleaner and more readable code for logging.
- **Built-in Features**: Includes features like log rotation and async logging out of the box.

### How to Use Loguru?

To use Loguru, you need to install it first, and then you can set up and start logging with minimal code.

### Installation

```
pip install loguru
```

### Basic Usage

**Import Loguru**

**Log Messages**

**Advanced Configuration**

You can add file logging, set rotation, and other advanced configurations as follows:

### Pros and Cons of Loguru

### Pros

- **User-Friendly**: Easy to set up and use.
- **Comprehensive**: Built-in features like log rotation and async logging.
- **Flexible**: Easily customizable to suit different needs.

### Cons

- **Learning Curve**: Some advanced features might require additional learning.
- **Third-party Integrations**: Fewer integrations compared to the built-in logging module.

### Example Usage Step by Step

**Basic Logging**

**Logging with Variables**

**File Logging with Rotation**

**Custom Formatting**

**Handling Exceptions**

### Conclusion

Loguru is a powerful and user-friendly logging library for Python that simplifies many aspects of logging. Its ease of setup, flexibility, and intuitive syntax make it a valuable tool for both beginners and experienced developers. While it has fewer third-party integrations than some alternatives, its built-in features and straightforward configuration make it a compelling choice for many applications.

```python
def divide(a, b):
    try:
        return a / b
    except ZeroDivisionError as e:
        logger.exception("Exception occurred")

divide(5, 0)
```

```python
logger.add("custom.log", format="{time} - {level} - {message}")
logger.info("This is a custom formatted log message")
```

```python
from loguru import logger

logger.add("app.log", rotation="1 week", retention="10 days")
logger.info("This will be logged to a file with rotation")
```

```python
name = "Alice"
age = 30
logger.info("User {name} is {age} years old", name=name, age=age)
```

```python
from loguru import logger

logger.info("This is an info message")
```

```python
logger.add("file.log", rotation="500 MB")  # Automatically rotate files when they reach 500 MB
```

```python
logger.debug("This is a debug message")
logger.info("This is an info message")
logger.warning("This is a warning message")
logger.error("This is an error message")
logger.critical("This is a critical message")
```

```python
from loguru import logger
```
