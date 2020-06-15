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
Example - Summation(1->n)
```sh
defmodule Series do
  def summation(n) do
    Enum.sum 1..n
  end
end
```

```sh
defmodule Series do
  def summation(n) when n<1 do 0
  def summation(n) do
    summation(n-1) + n
  end
end
```
One is a recurrsive approach(traditional), other one is an enumerated approach(elixir)

reduce and map approach
```sh
defmodule Math do
  def sum_list([head | tail], accumulator) do
    sum_list(tail, head + accumulator)
  end

  def sum_list([], accumulator) do
    accumulator
  end
end

IO.puts Math.sum_list([1, 2, 3], 0) #=> 6
```
