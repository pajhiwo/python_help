# Files

## Redirect output to file
Open an output file in “write” mode and the print the contents into that file, using sys.stdout attribute.
```python
import sys

sys.stdout = open('file', 'w')
print 'test'

# or

python redirect_output.py > outputfile.
```

## Open and read file
```python
with open("file-name", "r") as fp:  
    fileData = fp.read()  
#to print the contents of the file 
```
