# Fstrings
source: https://www.peterbe.com/plog/how-to-pad-fill-string-by-variable-python
General template:
```python
f/F"{variable/'text'[:[filler][align][length]]}"
#where:
# < left align
# > right align
# part related to aligning and filling is optional  


#examples
>>> print(f"{var}plus text")  
varrplus text
>>> print(f"{var:*<10}plus text")  
varr******plus text  
>>> print(f"{var:*>10}plus text")  
******varrplus text
# filler and len may be replaced by variables
>>> length = 10  
>>> filler = "*"
>>> print(f"{var:{filler}>{length}}plus text")  
******varrplus text
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIwMTE5MTM4Ml19
-->