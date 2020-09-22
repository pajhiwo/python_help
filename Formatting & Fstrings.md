# Fstrings
source: https://www.peterbe.com/plog/how-to-pad-fill-string-by-variable-python
General template:
```python
f/F"{variable/'text':[filler][adjusting][length]}"
#where:
# < left align
# > right align

#examples
>>> print(f"{var}plus text")  
varrplus text
>>> print(f"{var:*<10}plus text")  
varr******plus text  
>>> print(f"{var:*>10}plus text")  
******varrplus text
```
# Formatting
<!--stackedit_data:
eyJoaXN0b3J5IjpbOTQ5ODQ2NDIzXX0=
-->