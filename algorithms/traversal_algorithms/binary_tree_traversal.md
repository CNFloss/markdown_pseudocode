```
Structure Node:
  Value As Integer
  LeftChild As Node
  RightChild As Node

Function InOrderTraversal(current As Node):
  If current Not null:
    InOrderTraversal(current.LeftChild)
    Print(current.Value)
    InOrderTraversal(current.RightChild)

Function PreOrderTraversal(current As Node):
  If current Not null:
    Print(current.Value)
    PreOrderTraversal(current.LeftChild)
    PreOrderTraversal(current.RightChild)

Function PostOrderTraversal(current As Node):
  If current Not null:
    PostOrderTraversal(current.LeftChild)
    PostOrderTraversal(current.RightChild)
    Print(current.Value)

```
