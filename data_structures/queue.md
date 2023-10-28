```
Class Queue
  Items As List Of AnyType

  Function Enqueue(item As AnyType)
    Items.Add(item)

  Function Dequeue() As AnyType
    If Items.Length = 0
      Return Nil
    RemovedItem = Items.First()
    Items.RemoveFirst()
    Return RemovedItem

  Function Peek() As AnyType
    If Items.Length = 0
      Return Nil
    Return Items.First()

  Function IsEmpty() As Boolean
    Return Items.Length = 0

```
