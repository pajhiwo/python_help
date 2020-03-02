Supported by builtin `logging`
Can be configured to output other data (loglevel) with different formatting to console and log file:
```python
import logging
import logging.handlers

pd_logger = logging.getLogger("SomeLogger")
pd_logger.setLevel(logging.DEBUG)
file_handler = logging.handlers.RotatingFileHandler(
PyDriver.LOG_FILENAME, maxBytes=1024 * 1024 * 10, backupCount=5
)  # Up to 5 log files will be rotated every 10 MB
console_handler = logging.StreamHandler() # Configure what apperas on console
console_handler.setLevel(logging.INFO) # INFO and above will appear on console
file_handler.setLevel(logging.DEBUG) # DEBUG and above will appear in log file
file_formatter = logging.Formatter("%(asctime)s - %(lineno)s - %(funcName)s - %(levelname)s - %(message)s") # Formats of logs in log file. There is no formatter for console so they will look like prints statements
file_handler.setFormatter(file_formatter)
pd_logger.addHandler(file_handler)
pd_logger.addHandler(console_handler)
```
Calling this cause that following appears in console and log file:
```
```
Console:
```
```
Log file:
```
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNjUxNjU5MjcyLDEyNDgzNjUxMDJdfQ==
-->