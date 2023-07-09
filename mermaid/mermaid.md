# My mermaid adventure

## Mermaid diagram

[Diagram types](https://mermaid.js.org/intro/#diagram-types)

### Sequence

```mermaid
sequenceDiagram
    participant Alice
    participant Bob
    Alice->>John: Hello John, how are you?
    loop Healthcheck
        John->>John: Fight against hypochondria
    end
    Note right of John: Rational thoughts!
    John-->>Alice: Great!
    John->>Bob: How about you Bob? 
    Bob-->>John: Jolly bally good JJ!
```

### Flowchart

:::mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
:::

### Flowchart 2

```mermaid
flowchart TB
    c1-->a2
    subgraph ide1 [one]
    a1-->a2
    end
```

### Gantt diagram

```mermaid
gantt
dateFormat  YYYY-MM-DD
title Adding GANTT diagram to mermaid
excludes weekdays 2014-01-10

section A section
Completed task            :done,    des1, 2014-01-06,2014-01-08
Active task               :active,  des2, 2014-01-09, 3d
Future task               :         des3, after des2, 5d
Future task2               :         des4, after des3, 5d
```

### Mindmap

```mermaid
mindmap
  root((mindmap))
    Origins
      Long history
      ::icon(fa fa-book)
      Popularisation
        British popular psychology author Tony Buzan
    Research
      On effectiveness<br/>and features
      On Automatic creation
        Uses
            Creative techniques
            Strategic planning
            Argument mapping
    Tools
      Pen and paper
      Mermaid
```

### Git commits

```mermaid
gitGraph:
    commit "Ashish"
    branch newbranch
    checkout newbranch
    commit id:"1111"
    commit tag:"test"
    checkout main
    commit type: HIGHLIGHT
    commit
    merge newbranch
    commit
    branch b2
    commit
```

## Graphviz diagram

```graphwiz
graph graphname {
    a -- b -- c;
    b -- d;
}
```

```graphviz
graph graphname {
    a -- b -- c;
    b -- d;
}
```

```dot
graph graphname {
    a -- b -- c;
    b -- d;
}
```
