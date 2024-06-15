# Overview of Watchdog

## What is Watchdog?

Watchdog is a Python library and toolset designed to monitor filesystem events. It allows Python applications to monitor changes in the filesystem in a platform-independent manner.

- **Created:** Watchdog was created by Alex Quinn and Jan-Philip Gehrcke.
- **Purpose:** It was created to provide a simple API for monitoring filesystem events such as file creation, deletion, and modification.

---

## Alternatives

Here's a comparison table of Watchdog with some alternatives:

| Feature            | Watchdog                              | Pyinotify                       | Watchdog vs. Pyinotify                              |
| ------------------ | ------------------------------------- | ------------------------------- | --------------------------------------------------- |
| **Platform**       | Cross-platform                        | Linux only                      | Watchdog is cross-platform, Pyinotify is Linux-only |
| **API Simplicity** | Simple API                            | Complex API                     | Watchdog has a simpler API                          |
| **Dependencies**   | Pure Python, no external dependencies | Requires inotify system package | Watchdog has fewer dependencies                     |
| **Performance**    | Generally good                        | Very efficient for Linux        | Depends on use case and platform                    |
| **Maintained**     | Actively maintained                   | Not actively maintained         | Watchdog is actively maintained                     |

---

## Why Use Watchdog?

**Pros:**

- **Platform Independence:** Works across different operating systems.
- **Simplicity:** Easy-to-use API for monitoring filesystem events.
- **Active Development:** Actively maintained with regular updates.

**Cons:**

- **Limited to Python:** Watchdog is specific to Python applications.
- **Performance Variability:** Performance may vary across different platforms and use cases.

---

## How to Use Watchdog

## Installation:

### You can install Watchdog using pip:

```
pip install watchdog
```

### Basic Example Usage:

```python
import time
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler

class MyHandler(FileSystemEventHandler):
    def on_created(self, event):
        if event.is_directory:
            print(f"Directory created: {event.src_path}")
        else:
            print(f"File created: {event.src_path}")

if __name__ == "__main__":
    path = "/path/to/directory/to/monitor"
    event_handler = MyHandler()
    observer = Observer()
    observer.schedule(event_handler, path, recursive=True)
    observer.start()

    try:
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        observer.stop()

    observer.join()
```

### Advance Example Usage:

```python
import time
import logging
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler

# Setup logging
logging.basicConfig(level=logging.INFO,
                    format='%(asctime)s - %(message)s',
                    datefmt='%Y-%m-%d %H:%M:%S')

class MyHandler(FileSystemEventHandler):
    def on_any_event(self, event):
        if event.is_directory:
            if event.event_type == 'created':
                logging.info(f"Directory created: {event.src_path}")
            elif event.event_type == 'deleted':
                logging.info(f"Directory deleted: {event.src_path}")
            elif event.event_type == 'modified':
                logging.info(f"Directory modified: {event.src_path}")
        else:
            if event.event_type == 'created':
                logging.info(f"File created: {event.src_path}")
            elif event.event_type == 'deleted':
                logging.info(f"File deleted: {event.src_path}")
            elif event.event_type == 'modified':
                logging.info(f"File modified: {event.src_path}")
            elif event.event_type == 'moved':
                logging.info(f"File moved from {event.src_path} to {event.dest_path}")

if __name__ == "__main__":
    path = "/path/to/directory/to/monitor"
    event_handler = MyHandler()
    observer = Observer()
    observer.schedule(event_handler, path, recursive=True)
    observer.start()

    try:
        logging.info(f"Watching directory: {path}")
        while True:
            time.sleep(1)
    except KeyboardInterrupt:
        observer.stop()
        logging.info("Monitoring stopped by user.")

    observer.join()
```

### Explanation:

1.  **Imports:** Import necessary components from Watchdog.
2.  **Event Handler:** Define a custom event handler that inherits from `FileSystemEventHandler`.
3.  **Handler Methods:** Implement methods such as `on_created` to handle specific filesystem events.
4.  **Observer Setup:** Create an `Observer` instance and schedule the event handler to monitor a specific path recursively.
5.  **Start Monitoring:** Start the observer to begin monitoring filesystem events.
6.  **Keyboard Interrupt Handling:** Use a try-except block to handle keyboard interrupts (`Ctrl+C`) to stop the observer gracefully.
7.  **Observer Join:** Ensure the observer thread completes using `observer.join()`.

---

### Conclusion

Watchdog is a valuable tool for Python developers needing to monitor filesystem events efficiently across different operating systems. Its simplicity and active maintenance make it a preferred choice for many filesystem monitoring tasks in Python applications.

## Feel free to reach out if you have any questions or need help getting started!

Github: [https://0xaungkon.github.io/](https://0xaungkon.github.io/)

Linkedin: [https://www.linkedin.com/in/aungkon-malakar/](https://www.linkedin.com/in/aungkon-malakar/)

Facebook: [https://www.facebook.com/0xAungkon/](https://www.facebook.com/0xAungkon/)

---
