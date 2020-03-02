Supported by builtin `logging`
Can be configured to output other data (loglevel) with different formatting to console and log file:
```python
pd_logger = logging.getLogger("DriverLogger")
pd_logger.setLevel(logging.DEBUG)
file_handler = logging.handlers.RotatingFileHandler(
PyDriver.LOG_FILENAME, maxBytes=1024 * 1024 * 10, backupCount=5
)
console_handler = logging.StreamHandler()
console_handler.setLevel(logging.INFO)
file_handler.setLevel(logging.DEBUG)
file_formatter = logging.Formatter("%(asctime)s - %(lineno)s - %(funcName)s - %(levelname)s - %(message)s")
file_handler.setFormatter(file_formatter)
pd_logger.addHandler(file_handler)
pd_logger.addHandler(console_handler)
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEyNTQxNzg3MiwxMjQ4MzY1MTAyXX0=
-->