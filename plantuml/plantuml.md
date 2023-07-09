# Render PlantUML inline inside a Markdown file

## Guide to PlatnUML

[The Hitchhiker’s Guide to PlantUML!](https://crashedmind.github.io/PlantUMLHitchhikersGuide/index.html)

## Sequence diagram

A PlantUML diagram:

```plantuml
@startuml
Bob -> Alice : hello
Alice -> Bob : Just **bog off** will you!?
Alice -> Bob : Please
Bob -> Alice : Well that is __very__ nice!
@enduml
```

## uml: sequence diagram

Here I will embed PlantUML markup to generate a sequence diagram.

I can include as many plantuml segments as I want in my Markdown, and the diagrams can be of any type supported by PlantUML.

```plantuml
@startuml
    skinparam backgroundColor #EEEBDC
    skinparam handwritten true
    actor Customer
    Customer -> "login()" : username & password
    "login()" -> Customer : session token
    activate "login()"
    Customer -> "placeOrder()" : session token, order info
    "placeOrder()" -> Customer : okay dokey
    Customer -> "logout()"
    "logout()" -> Customer : kapai
    deactivate "login()"
@enduml
```

## Component diagram

[Component Diagram](https://plantuml.com/component-diagram)

```plantuml
@startuml

[First component]
[Another component] as Comp2
component Comp3
component [Last\ncomponent] as Comp4
[First component] --> Comp2
Comp3 <..> Comp4
Comp4 -- [First component]
Comp2 --> Comp3
note right of Comp3: Better come up with a better name for this
@enduml
```

```plantuml
@startuml
' Square brackets means a component
[First component] --> Comp2
Comp3 --> HTTP

' Explicitly declare a component
component Comp4
Comp4 --> [Comp5]
[Comp6]
@enduml
```

## Grouping components

From ??

```plantuml
@startuml

package "Some Group" {
  HTTP - [First Component]
  [Another Component]
}

node "Other Groups" {
  FTP - [Second Component]
  [First Component] --> FTP
}

cloud {
  [Example 1]
}


database "MySql" {
  folder "This is my folder" {
    [Folder 3]
  }
  frame "Foo" {
    [Frame 4]
  }
}


[Another Component] --> [Example 1]
[Example 1] --> [Folder 3]
[Folder 3] --> [Frame 4]

@enduml
```


## Sudoku

```plantuml

@startuml Sudoku Puzzle
sudoku
@enduml

```

## Flowchart

A flow chart?

This form of `mermaid` diagram doesn't work with `plantuml`.

```plantuml
@startuml

flowchart TB
    c1-->a2
    subgraph ide1 [one]
    a1-->a2
    end
@enduml
```

It should look like:

![flowchart example](flowchart%20example%20small.png)

A `digraph` attempt at the same diagram:

```plantuml
@startuml
digraph foo {
    c1 [shape=box]
    subgraph cluster_one {
        graph [ label="one" ]
        a1 [shape=box]
        a2 [shape=box]
    }
    c1 -> a2
    a1 -> a2
}
@enduml
```

```plantuml
@startuml
rectangle c1
rectangle one {
    top to bottom direction
    rectangle a1
    rectangle a2
}
c1 --> a2 
a1 --> a2

@enduml
```

The following was generated with the help of ChatGPT.

```plantuml
@startuml
rectangle "Group" #lightgreen {
  rectangle "Two" #lightblue
  rectangle "Three" #lightblue
}
rectangle "One" #lightyellow
One --> Three
Two --> Three
@enduml
```

Bing helped create this component diagram:

```plantuml
@startuml
component One <<Application>> #FFC0CB
component Two <<Application>> #FFC0CB
component Three <<Application>> #FFC0CB

One --> Two
Two --> Three
Three --> One
@enduml
```

## Digraph

```plantuml
@startuml
digraph foo {
  node [style=rounded]
  node1 [shape=box]
  node2 [fillcolor=yellow, style="rounded,filled", shape=diamond]
  node3 [shape=record, label="{ a | b | c }"]

  node1 -> node2 -> node3
}
@enduml
```

## Another digraph

```plantuml
@startuml
digraph G {
        compound=true

        subgraph cluster_family1 {
                graph [ label="Family 1"; ]
                subgraph cluster_genus1_3 {
                        graph [ label="Genus 1.3"; ]
                        species_12 [label="Species 1.3.2"]
                        species_13
                }
                subgraph cluster_genus1 {
                        graph [ label="Genus 1"; ]
                        species_2 [label="Species 2"]
                        species_1 [label="Species 1"]
                }
                subgraph cluster_genus2 {
                        graph [ label="Genus 2"; ]
                        species_4
                        species_3
                }
        }
        subgraph cluster_family2 {
                graph [ label="Family 2"; ]
                subgraph cluster_genus3 {  // fixed duplicate name
                        graph [ label="Genus 3"; ]
                        species_6
                        species_5
                }
        }
        species_2 -> species_4 [ ltail=cluster_genus1 lhead=cluster_genus2
            # style=invis
        ] # changed head to tail??
        species_5 -> species_4 [ style=dotted]
}
@enduml
```

## Archimate

In theory the following `div` generates a hidden diagram. Then the later image inclusion displays it.

An alternative [suggestion](https://gist.github.com/noamtamim/f11982b28602bd7e604c233fbe9d910f) is to surround the uml wiht `<!--    -->`.

See [](https://gist.githubusercontent.com/noamtamim/f11982b28602bd7e604c233fbe9d910f/raw/a30512d25ae52b61e9c1e904f9713488288fd910/sample.md)

<div hidden>

```plantuml
@startuml TestArchimateDiagram
archimate #Technology "VPN Server" as vpnServerA <<technology-device>>

sprite $bProcess jar:archimate/business-process
sprite $aComponent jar:archimate/application-component
sprite $aService jar:archimate/application-service

rectangle GO #lightgreen
rectangle STOP #red
rectangle WAIT #orange


rectangle "Component for John" <<$aComponent>> #Application
rectangle "Component for MSD" <<$aComponent>> #Business

@enduml
```

</div>

## Display diagram

In theory, the diagram will display here:

![Diagram generated elsewhere](TestArchimateDiagram.svg)

## Big archimate example

```plantuml
@startuml

@startuml
skinparam rectangle<<behavior>> {
    roundCorner 25
}
sprite $bProcess jar:archimate/business-process
sprite $aService jar:archimate/application-service
sprite $aComponent jar:archimate/application-component

rectangle "Handle claim"  as HC <<$bProcess>><<behavior>> #Business
rectangle "Capture Information"  as CI <<$bProcess>><<behavior>> #Business
rectangle "Notify\nAdditional Stakeholders" as NAS <<$bProcess>><<behavior>> #Business
rectangle "Validate" as V <<$bProcess>><<behavior>> #Business
rectangle "Investigate" as I <<$bProcess>><<behavior>> #Business
rectangle "Pay" as P <<$bProcess>><<behavior>> #Business

HC *-down- CI
HC *-down- NAS
HC *-down- V
HC *-down- I
HC *-down- P

CI -right->> NAS
NAS -right->> V
V -right->> I
I -right->> P

rectangle "Scanning" as scanning <<$aService>><<behavior>> #Application
rectangle "Customer admnistration" as customerAdministration <<$aService>><<behavior>> #Application
rectangle "Claims admnistration" as claimsAdministration <<$aService>><<behavior>> #Application
rectangle Printing <<$aService>><<behavior>> #Application
rectangle Payment <<$aService>><<behavior>> #Application

scanning -up-> CI
customerAdministration  -up-> CI
claimsAdministration -up-> NAS
claimsAdministration -up-> V
claimsAdministration -up-> I
Payment -up-> P

Printing -up-> V
Printing -up-> P

rectangle "Document\nManagement\nSystem" as DMS <<$aComponent>> #Application
rectangle "General\nCRM\nSystem" as CRM <<$aComponent>>  #Application
rectangle "Home & Away\nPolicy\nAdministration" as HAPA <<$aComponent>> #Application
rectangle "Home & Away\nFinancial\nAdministration" as HFPA <<$aComponent>>  #Application

DMS .up.|> scanning
DMS .up.|> Printing
CRM .up.|> customerAdministration
HAPA .up.|> claimsAdministration
HFPA .up.|> Payment

legend left
Example from the "Archisurance case study" (OpenGroup).
See
====
<$bProcess> :business process
====
<$aService> : application service
====
<$aComponent> : application component
endlegend
@enduml
@enduml
```

### List Archimate stuff

```plantuml
@startuml
listsprite
@enduml
```

```plantuml
@startuml
archimate #Technology "VPN Server" as vpnServerA <<technology-device>>
archimate #Application "Job Listings" <<application-component>>
rectangle "Job Search" <<component>>
@enduml
```

### Relationship types

```plantuml
@startuml
left to right direction
skinparam nodesep 4
!include <archimate/Archimate>
Rel_Triggering(i15, j15, Triggering)
Rel_Specialization(i14, j14, Specialization)
Rel_Serving(i13, j13, Serving)
Rel_Realization(i12, j12, Realization)
Rel_Influence(i11, j11, Influence)
Rel_Flow(i10, j10, Flow)
Rel_Composition(i9, j9, Composition)
Rel_Association_dir(i8, j8, Association_dir)
Rel_Association(i7, j7, Association)
Rel_Assignment(i6, j6, Assignment)
Rel_Aggregation(i5, j5, Aggregation)
Rel_Access_w(i4, j4, Access_w)
Rel_Access_rw(i3, j3, Access_rw)
Rel_Access_r(i2, j2, Access_r)
Rel_Access(i1, j1, Access)
@enduml

```
