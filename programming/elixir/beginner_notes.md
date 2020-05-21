# Elixir notes

## String Operations
Replace characters in a string using regex 
    
```
# remove / in the given string
String.replace("1000 cfu/ml", ~r"[a-z /]", "")
# remove ! in the string
String.replace(s,~r"[!]", "")
```

## Enumeration

Multiply all the elements of a list
```
Enum.reduce(arr,fn(i,res) -> res*i end)
```
