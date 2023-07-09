# DESP

## Mermaid diagram

### Sequence

```mermaid
graph LR
    Job_seekers(Job seekers) -->|uses| Online_system(Online system)
    Online_system -->|communicates with| DESP(DESP)
    DESP -->|depends on| CMS(CMS)
    Employers(Employers) -->|uses| Online_system
```

## Graphwiz diagram

It is not actually `graphwiz`, should be `graphviz`.

See the [Graphviz](https://graphviz.org/) website.

```graphwiz
digraph G {
    Job_seekers [label="Job seekers"]
    Online_system [label="Online system"]
    DESP [label="DESP"]
    CMS [label="CMS"]
    Employers [label="Employers"]

    Job_seekers -> Online_system [label="uses"]
    Online_system -> DESP [label="communicates with"]
    DESP -> CMS [label="depends on"]
    Employers -> Online_system [label="uses"]
}
```

```graphviz
digraph G {
    Job_seekers [label="Job seekers"]
    Online_system [label="Online system"]
    DESP [label="DESP"]
    CMS [label="CMS"]
    Employers [label="Employers"]

    Job_seekers -> Online_system [label="uses"]
    Online_system -> DESP [label="communicates with"]
    DESP -> CMS [label="depends on"]
    Employers -> Online_system [label="uses"]
}
```

Bing says the `dot` is the same as `graphviz`.

```dot
digraph G {
    Job_seekers [label="Job seekers"]
    Online_system [label="Online system"]
    DESP [label="DESP"]
    CMS [label="CMS"]
    Employers [label="Employers"]

    Job_seekers -> Online_system [label="uses"]
    Online_system -> DESP [label="communicates with"]
    DESP -> CMS [label="depends on"]
    Employers -> Online_system [label="uses"]
}
```

## From the extension example

The `graphviz` examples render on first preview but the rendering disappears once a change is made. A refresh of the preview also works.

```graphviz
digraph finite_state_machine {
    rankdir=LR;
    size="8,5"

    node [shape = doublecircle]; S;
    node [shape = point ]; qi

    node [shape = circle];
    qi -> S;
    S  -> q1 [ label = "a" ];
    S  -> S  [ label = "a" ];
    q1 -> S  [ label = "a" ];
    q1 -> q2 [ label = "ddb" ];
    q2 -> q1 [ label = "b" ];
    q2 -> q2 [ label = "b" ];
}
```
