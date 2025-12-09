# Layout

> *It's true that when diagram is big (or very big) manual placement
> could be useful. However and unfortunately, this is against PlantUML
> concept* <https://forum.plantuml.net/977>
>
> Wrangling diagram elements to an exact position or layout is not what
> PlantUML is for.
>
> However, there are **some layout tweak mechanisms that should be used
> sparingly**. These are described here.

## Arrows for Layout

We can specify a connection direction as follows and this affects the
diagram layout:

| Text                | Direction                           |
|--------------------|-------------------------------------|
| `->`               | horizontal left to right             |
| `-->`              | vertical top to bottom               |
| `-up->` or `-u->`  | vertical bottom to top               |
| `-down->` or `-d->`| vertical top to bottom               |
| `-left->` or `-l->`| horizontal right to left             |
| `-right->` or `-r->`| horizontal left to right            |
| `--[norank]>`      | make a connection less important     |
| `--[hidden]>`      | hidden                               |
| `-[hidden]d->`     | hidden with direction e.g. down      |
| `--->` or `---->` or `----->` ... | varying arrow lengths; add dashes to make line longer |



> The order in which diagram elements are defined can also impact how
> they are laid out.
>
> Arrow head stypes per <https://plantuml.com/sequence-diagram> are for
> sequence diagrams only i.e. won't work in our component diagram
> examples.

## up down left right



![](/PlantUML%20features/layout/arrows.png)




```
@startuml

rectangle Arrows
rectangle Up
rectangle Down
rectangle Left
rectangle Right

Arrows -u-> Up 
Arrows -d-> Down
Arrows -l-> Left
Arrows -r-> Right

@enduml
```




## left to right direction



![](/PlantUML%20features/layout/left2right.png)




```
@startuml

left to right direction
'top to bottom direction

rectangle Arrows
rectangle A
rectangle B
rectangle C
rectangle D
rectangle E
rectangle F

Arrows --> A 
Arrows --> B
Arrows --> C
Arrows --> D
Arrows --[hidden]> E

@enduml
```




## top to bottom direction



![](/PlantUML%20features/layout/top2bottom.png)




```
@startuml

'left to right direction
top to bottom direction

rectangle Arrows
rectangle A
rectangle B
rectangle C
rectangle D
rectangle E
rectangle F

Arrows --> A 
Arrows --> B
Arrows --> C
Arrows --> D
Arrows --[hidden]> E

@enduml
```



## hidden

> Note that the location of E is determined by a hidden arrow. Whereas F
> is floating i.e. not connected by an arrow so it can go anywhere.

## nodesep and ranksep



![](/PlantUML%20features/layout/nodesepranksep.png)




```
@startuml

'skinparam nodesep 10
'skinparam ranksep 20

rectangle Arrows
rectangle A
rectangle B
rectangle C
rectangle D
rectangle E
rectangle F

Arrows -[bold]-> A 
Arrows -[#pink,dashed,thickness=10]-> B
Arrows -[#4567ff,dotted]-> C
Arrows --> D
E ---> C

@enduml
```




![](/PlantUML%20features/layout/nodesepranksep1.png)



```
@startuml

skinparam nodesep 5
'skinparam ranksep 20

rectangle Arrows
rectangle A
rectangle B
rectangle C
rectangle D
rectangle E
rectangle F

Arrows -[bold]-> A 
Arrows -[#pink,dashed,thickness=10]-> B
Arrows -[#4567ff,dotted]-> C
Arrows --> D
E ---> C

@enduml
```




![](/PlantUML%20features/layout/nodesepranksep2.png)




```
@startuml

'left to right direction
'top to bottom direction

'skinparam nodesep 10
skinparam ranksep 150

rectangle Arrows
rectangle A
rectangle B
rectangle C
rectangle D
rectangle E
rectangle F

Arrows -[bold]-> A 
Arrows -[#pink,dashed,thickness=10]-> B
Arrows -[#4567ff,dotted]-> C
Arrows --> D

'long arrow for no good reason 
E ---> C 

@enduml
```


## together

D,E are forced together.

E-C is specified as a very long arrow



![](/PlantUML%20features/layout/together.png)




```
@startuml

rectangle Arrows
rectangle A
rectangle B
rectangle C
together {
rectangle D
rectangle E
}
rectangle F


Arrows -[bold]-> A 
Arrows -[#4567ff,dotted]-> C
Arrows -[#pink,dashed,thickness=10]-> B
Arrows --> D
E ---------> C

@enduml
```


## linetype polyline ortho

Either of the following can be added to a diagram:

- "skinparam linetype polyline"
- "skinparam linetype ortho"

See `Create Real Life AWS Diagrams` for practical examples of where
these are used.

As at May 2020, it looks like there can be an issue using ortho.
Specifically the label being too distant from the line.

- In our
  [AWSExample](http://www.plantuml.com/plantuml/uml/VL1BRnD13BxFhp1x8KXa8mfS8bGrH1Ng0GbfUPmdCsxMYkV1F99MLVyxJfPLAhJailRuUtpstkIYKwcErIloXgj5-AGFcMcpMFtgri6vuAydiOvSPBedj6qK_GH9rB4MN6Zc_r5Ss11VP6pHOz9yYV8bXHhlJF3v1KkzpZloKIVjWCbZUOm8-vZD9103FnuVQW8BgVH1gQZDJcyH6haTrXogRU19tQwlPftJ5X_UGZCqq67Qay569j2yKSzA_SYOykpqbU6fZkZtf2qL2bxpKOTfjhAt3wRNVej2MLaONwFYw-cVpOOYiszrmvHxJA1ZX93WW9kHEoJ3t8Q3dr_3e5d2knP-KgQI_vh1FD6sBy8uXo_XgeMkw5H0LtFSK9t1is2uUGdlM_XC5XB-hfWBBAJBCVYCQc30dF6-lDZXWxZtuI29uvB_MdviuSv5ySaIBew6oUoaaiz5Cqk7U_G5diPGii_g1hsjZly0)
  the label "4. Show Ad" is too far from the line to be useful.
- issue seen by other users:
  <https://forum.plantuml.net/1608/is-it-possible-to-only-use-straight-lines-in-a-class-diagram>
