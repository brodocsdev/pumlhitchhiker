# Standard Library - What We Have And What We Want

## Observations on Standard Library

> This page is superseded by an RFC:
> <https://github.com/plantuml/rfc-for-standard-plantuml-stdlib> to
> solicit user input, but I'll leave it here for reference/context.
>
> The Observations, Requirements, and User Stories here allow us to
> create a new PlantUML Stdlib to empower the user per todoref
>


| #                       | Observation |
|-------------------------|-------------|
| **OBV_DEFINE_DEPRECATED** | Macros use `define` and `definelong` which are deprecated per below |
| **OBV_DRY** | DRY (Don't Repeat Yourself). The macros are repeated:<br><br>within a file – repeat the macro to add each new parameter<br><br>across files – the macro content is largely the same, but the macro name changes to specify the icon to use |
| **OBV_CLOSE_COUPLING** | Macros are defined in the icon file for each icon.<br><br>The parameters, and order of parameters, is fixed. |
| **OBV_CONSISTENCY** | **icon sizes**<br>- some have multiple sizes<br>- for those that have one size, it is not standard/common with the other stdlib libraries<br><br>**icon files**<br>- some break up the icons into category sub-directories, some don't<br>- some have an `all.puml` file that includes all sprite content per category, some **don’t** |
| **OBV_NO_SCALE** | There’s no way to scale the icons from the macros (`!define` statements) except for Material.<br><br>PlantUML does support scaling per <https://forum.plantuml.net/4267/scaling-of-the-sprites-or-images>.<br><br>Support for scaling stereotypes is available since March 2019. |
| **OBV_NO_TEXTATTRIB** | There’s no way to change the size, colour, etc. of the text description, label, or technology fields. |
| **OBV_3PARAMS_MIN** | At least 3 parameters are required and are rendered in the diagrams:<br><br>`!define Batch(e_alias, e_label, e_techn)`<br><br>Macros force a user to specify things they may not care about. For example, to specify color in this macro, the user must also specify preceding parameters.<br><br>`!define WHATEVER(_alias, _label, _shape, _color) ENTITY(_shape,_color,whatever,_label,_alias,WHATEVER)`<br><br>So if we want a colored or scaled icon only (with no label or technology), we must implement it ourselves. |
| **OBV_ALL_PUML** | Some libraries have an `all.puml` that includes all icons and their macros for a category/subset.<br><br>This allows including all icons via a single file instead of one include per icon. |



> The following software principles should apply
>
> > - Loose Coupling, High Cohesion (Consistency)
> > - DRY (Don't Repeat Yourself)
> > - Open/Closed Principle (OCP) “open for extension” but “closed to
> >   modification” i.e. not have to change old macros to implement new
> >   behavior. New Macros are defined instead, that don't break
> >   existing user code (SOLID).

## Macro Definitions

Macros define the following

> 1.  The superset of parameters
>
>     > 1.  sprite
>     > 2.  color
>     > 3.  scale (material library only)
>     > 4.  shape (Type 1 (e_type), 4 (\_shape))
>     > 5.  technology
>     > 6.  description
>     > 7.  label
>
> 2.  Fixed
>
>     > 1.  Text Size
>     > 2.  Text Order

## What a User Wants In A Standard Library


| #                   | Requirement                                                                                                                                                                                                                                                                                                                                                  |
|---------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **REQ_CONSISTENCY** | Consistency of macros, files, sizes                                                                                                                                                                                                                                                                                                                          |
| **REQ_ONLY_CARE**   | Specify the things they care about<br><br>Default values specified when the icons are built, but the ones the user cares about can be overridden by the user in their diagram file (at runtime)                                                                                                                        |
| **REQ_DECOUPLE**    | Decoupling of the sprite (the image), from the decoration (text, shape, color, scale etc...)<br><br>To benefit from other people's work e.g. if a new parameter or decoration/theme is added they like, they want to use it in their diagrams<br><br>Future Proofing with backwards compatibility: new functionality can be added to the sprite library, but the user's existing code will still work with this new library |
| **REQ_CATEGORY**    | Grouping of icons into categories.<br><br>A user can include a file for that category that includes all the icons (and not have to include a file for every icon)                                                                                                                                                      |
| **REQ_CONTRIBUTE**  | To be able to easily share / contribute<br><br>their icon set<br><br>their theme or style or layout                                                                                                                                                                                                                                                          |

## User Stories


| #                | As a User, I want X, so I am empowered to do Y                                                                                                                                                                                                                                                                                                                                                 |
|------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **US_HIGHLIGHT** | To highlight certain parts of a diagram<br><br>so I can show the relevant or important parts in the context of an overall diagram<br><br>e.g. a diagram may have 10 icons/components, but I want to highlight the ones being discussed or changed in my current system                                                                                      |
| **US_THEME**     | To use, or create, a theme,<br><br>so I can create diagrams consistent with my other (personal, organisation, company) documentation.                                                                                                                                                                                                                                                           |
| **US_ICONSET**   | To use, or create and contribute, an icon set easily<br><br>so I have all the icons I need for my diagrams                                                                                                                                                                                                                                                                                     |
