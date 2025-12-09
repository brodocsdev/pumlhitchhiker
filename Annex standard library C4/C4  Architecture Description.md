# C4 Lightweight Software Architecture Description Method

## Introduction

> *Big design up front is dumb, but doing no design up front is even
> dumber.* Dave Thomas

The [C4 Model](https://c4model.com/) is a lightweight software
architecture description method. It consists of a set of 4 diagrams that
describe the **static** structure of a software system.

Overall, C4 strives for clarity and communication of the story, and
follows [Shneiderman's
mantra](http://www.ifp.illinois.edu/nabhcs/abstracts/shneiderman.html):

> *Overview first, zoom and filter, then details-on-demand*

It is not formal UML e.g. the UML actor stickman is deliberately not
used as it causes confusion between a person or a system.

> Multiple independent views of a system are better than just one view.
>
> PlantUML sequence diagrams can give a good **dynamic** view of a
> system. Similar to C4, they can start at the top level, and zoom into
> the details in different diagrams.

<figure>
<img src="./c4.png" alt="./c4.png" />
<figcaption>The 4 C's</figcaption>
</figure>

| The **4C's**          |
|-----------------------|
| **Context**           |
| **Container**         |
| **Component**         |
| **Classes (or Code)** |

## CheatSheet

The
[CheatSheet](http://www.codingthearchitecture.com/2017/04/27/visualising_and_documenting_software_architecture_cheat_sheets.html)
gives a good summary of the C4 model and diagrams.

## Video Presentation

See [youtube video from NDC2017
conference](https://www.youtube.com/watch?v=Ym9nhVZs89o) by Simon Brown
on C4 for visualisation.

## Related Methods

There are a number of related models and templates:

### 4+1 model

C4 is inspired by [the 4+1 model for software
architecture](https://en.wikipedia.org/wiki/4%2B1_architectural_view_model)

### [ARC42](https://arc42.org//)

C4 can be combined with arc42 documentation template. The diagrams map
as follows:

| Arc42                         | C4                     |
|-------------------------------|------------------------|
| Context and Scope             | System Context diagram |
| Building Block View (level 1) | Container diagram      |
| Building Block View (level 2) | Component diagram      |
| Building Block View (level 3) | Class diagram          |

### Data-flow diagrams

[Data-flow diagrams
(DFD)](https://en.wikipedia.org/wiki/Data-flow_diagram) (to describe
data **activity**) use a similar hierarchical approach starting with the
contextual DFD0. They use a multi-level numbering scheme - DFD0: 1
-DFD1: 1.1., 1.2, - DFD2: 1.1.1, 1.1.2,

### Books

These books, written by
\[@simonbrown\](<https://twitter.com/simonbrown>), are available to buy
from <https://leanpub.com/visualising-software-architecture>.

![Book1](./swarchv1.png) ![Book2](./swarchv2.png)
