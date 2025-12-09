# About PlantUML



![](/res/plantumllogo.png)


<p align="center">
Where system diagrams meet system reality
</p>
<p></p>
<p></p>
<br/>
<br/>
<br/>

[PlantUML](https://www.plantuml.com/) is better known for UML-type
diagrams (sequence, use case, state,...) and other non-UML diagrams
(wireframes, mindmaps, gantt...)

- It has a simple intuitive syntax that makes it quick and easy to
  create/share/modify such diagrams.

[PlantUMLStdlib](https://plantuml.com/stdlib) is not so well known

- A simple intuitive syntax makes it quick and easy to create diagrams
  with icons.

## Diagrams As Code

PlantUML diagrams are "Diagrams as Code" in PlantUML syntax.

There are many **presentation** and **drawing** tools out there. And
these allow the user full control over the diagram so generally result
in prettier diagrams that can convey more information to the audience at
that **point in time**.

But that point in time passes, and pretty pictures can quickly become
out-of-date and, ironically, misinforming if they don't match the
reality of the system they are describing. This is especially so if one
team is drawing the pretty pictures, and another team is writing the
software/implementing the system.

Having diagrams as code that can live beside the system code, that the
stakeholders are equally comfortable editing and viewing, reduces the
gap i.e. **"Where system diagrams meet system reality"**

Diagrams-As-Code fits with the "Everything-as-Code" movement.

And once you have your diagram as code, you can start using that diagram
code for other things e.g. automated analysis and feedback based on
recognised patterns.

## Shared Lexicon of Understanding

Such "*icon diagrams*" are increasingly popular as functionality moves
up the stack and a standard set of off-the-shelf components becomes
available ala Cloud, Everything-As-A-Service, Serverless.....

Companies like AWS, Google, Microsoft publish architecture icon sets for
these building blocks for architecture diagrams:

1.  <https://aws.amazon.com/architecture/icons/>
2.  <https://cloud.google.com/icons>
3.  <https://www.microsoft.com/en-us/download/details.aspx?id=41937>

These are the types of diagrams used for describing architectures as we
see in [Create Real Life AWS Diagrams](/docs/aws/aws.md) where we recreate diagrams from
the AWS architecture blog.

- These establish a shared lexicon of understanding and allow users to
  focus on the things they're trying to do.
- They can also be understood by a broad audience, especially the
  customer.
- They enable **lightweight just-enough**
  [AgileModeling](http://agilemodeling.com/essays/barelyGoodEnough.html)
  in a way that meets
  [AgileModelingBP](https://tdan.com/best-practices-for-agile-documentation/18936)

These building block icons can be used with

1.  architecture diagrams to give an overview of the building blocks and
    how they are connected
2.  [C4 Lightweight Software Architecture Description Method ](../C4/c4.md) to give static views at different levels
3.  sequence diagrams to give dynamic views at different levels

## Interview with Arnaud Roques (creator of PlantUML)

> **💡 Tip:** [A coffee with Arnaud Roques (creator of
> PlantUML)](https://modeling-languages.com/interview-plantuml/) gives a
> good background to PlantUML from the man himself.

## Useful PlantUML Links

> **💡 Tip:** See <https://crashedmind.github.io/plantuml.github.io/> for some
> useful PlantUML links.
