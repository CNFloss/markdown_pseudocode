```
Class GraphNode
  Value As Integer
  Neighbors As List Of GraphNode

Class Graph
  Nodes As List Of GraphNode

  Function AddNode(value As Integer) As GraphNode
    NewNode As New GraphNode
    NewNode.Value = value
    Nodes.Add(NewNode)
    Return NewNode

  Function AddEdge(node1 As GraphNode, node2 As GraphNode)
    node1.Neighbors.Add(node2)
    node2.Neighbors.Add(node1)  // For an undirected graph. Remove this line for directed graphs.

```
