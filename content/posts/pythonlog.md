+++
date = '2025-03-05T12:30:00+05:00'
title = 'The Art of Logging In Python!'
tags = ['python', 'github', 'hugo']
+++

Logging is a means of tracking events that happen when some software runs. It is an essential aspect of software development that helps in debugging, monitoring, and maintaining applications.

Python provides a built-in logging module that makes it easy to track events and errors in your code

## Why Use Logging?

Many beginners use print() statements for debugging, logging provides a better way to record messages, debug issues, and monitor applications.

- `Severity Levels:` Logging allows categorization of messages by severity (DEBUG, INFO, WARNING, ERROR, CRITICAL).

- `Configurability:` You can easily change logging levels, formats, and destinations without modifying the code.

- `Performance:` Logging can be written to files, reducing console clutter and making debugging easier.

### Advantages:

Logging is useful for:

- `Debugging:` Helps identify and fix issues in your code.

- `Monitoring:` Tracks application behavior over time.

- `Error Handling:` Provides useful error messages and tracebacks.

- `Performance Analysis:` Measures execution time and performance bottlenecks.

- `Storage:` Saves logs for future analysis.

## Getting Started with Logging

### Basic Example: 

Python’s logging module provides a simple way to log messages. For example:

```python
import logging

# configuring logging 
logging.basicConfig(level=logging.DEBUG)

# log messages
logging.info("This is a debug message.")
logging.info("This is an informational message")
logging.warning("This is a warning message")
logging.error("This is an error message")
logging.critical("This is a critical message")
```
### Understanding Log Levels

The `logging` module provides five different levels of severity:

| Level    | Numeric Value | Description |
|----------|--------------|-------------|
| `DEBUG`  | 10           | Detailed information, useful for debugging |
| `INFO`   | 20           | General information about program execution |
| `WARNING`| 30           | Indication of potential issues |
| `ERROR`  | 40           | A serious problem occurred |
| `CRITICAL` | 50         | A critical error that may cause a system crash |

By default, Python’s logging module displays messages of level WARNING and above.

## Configuring Logging

You can customize logging using `basicConfig()`. For example:

```python
logging.basicConfig(
    level=logging.DEBUG,
    format='%(asctime)s - %(levelname)s - %(message)s',
    datefmt='%Y-%m-%d %H:%M:%S'
)
```

### Logging to a File

Instead of printing logs to the console, you can save them to a file:

```python
logging.basicConfig(
    filename='app.log',
    level=logging.DEBUG,
    format='%(asctime)s - %(levelname)s - %(message)s',
    datefmt='%Y-%m-%d %H:%M:%S'
)
```

### Formatting Logs

You can customize the log message format using `format`:

```python
logging.basicConfig(
    format='%(levelname)s: %(message)s'
)
logging.warning("This is a formatted warning message.")
```

### Common format specifiers:

- `%(asctime)s` - Timestamp of the log message
- `%(levelname)s` - Log level (INFO, WARNING, etc.)
- `%(message)s` - The actual log message
- `%(filename)s` - Name of the source file
- `%(lineno)d` - Line number where the log was generated


## Advanced Logging Features


For more control over logs, the `logging` module allows creating separate loggers `handlers`, and `formatters`for different modules



## Best Practices for Logging

- **Use appropriate log levels**: Don't log everything as `DEBUG` or `INFO`.
- **Avoid logging sensitive data**: Logs may be stored and accessed by others.
- **Use structured logging**: Format logs in a way that makes them easy to analyze.
- **Rotate log files**: Prevent logs from growing too large using `RotatingFileHandler`.
- **Use separate log files for different purposes**: Keep error logs separate from general logs.

## Conclusion

Logging in Python is a powerful tool that helps track, debug, and analyze code execution. By understanding logging levels, configurations, and best practices, you can improve debugging, monitoring, and error handling in your applications.

Start implementing logging in your projects today and make your debugging process smoother! 🚀
