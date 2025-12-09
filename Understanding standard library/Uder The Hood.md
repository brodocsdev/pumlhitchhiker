# PlantUML Stdlib Under The Hood

> Below are the steps I took to understand the PlantUML Standard Library
> Macros.
>
> - It's a step-by-step in the dark - taking small validated steps.
> - The steps are listed here because it's educational and interesting.
> - **You should not, and don't have to, follow these steps.**
> - Based on the understanding gained, there's a better way to go.
>
> See `Standard Library - What We Have And What We Want`

## Goal

1.  Look under the hood of the generated plantuml icon files from
    <https://github.com/awslabs/aws-icons-for-plantuml> to understand
    them better - from first principles e.g.
    <https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/Compute/Batch.puml>

2.  To confirm understanding

    > - a new bare-minimum macro will be created that requires only 1
    >   parameter <span class="title-ref">!define Batch(e_alias)</span>
    > - a new macro will be added to allow scaling the icon size

## Steps to Understanding

### Using the sprite directly

"Batch" is defined in
<https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/Compute/Batch.puml>)
ala

    sprite $Batch [64x64/16z] {...



![](/StdlibUnderTheHood/1.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>

rectangle "<$Batch>" 

'NOTE that if we add a more than one call - nothing happens! We're missing an "as x"
rectangle "<$Batch>" 

@enduml

```


### Add an “as whatever”



![](/StdlibUnderTheHood/2.png)





```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>

rectangle "<$Batch>" 

'NOTE that if we add a more than one call - nothing happens! Need to change the second one to "as whateverElse"
rectangle "<$Batch>" as whatever
rectangle "<$Batch>" as whatever
@enduml
```





### Bare Minimum

Extract the sprite from the Batch.puml

Note that plantuml needs the @startuml and @endumlto recognize the file
as a plantuml diagram i.e. it won’t work without these



![](/StdlibUnderTheHood/3.png)





```
@startuml

sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}
@enduml


```




#### Bare Minimum by including Batch.puml

The result is the same.



![](/StdlibUnderTheHood/3.1.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>

@enduml
```



#### Illegal Bare Minimum by including all.puml

Note: This is not valid plantuml as it does not contain any elements.

- The VSCode Plantuml extension will happily render this in preview
  mode. But VSCode Plantuml extension export will fail
- Plantuml call will generate a blank output.


```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/all.puml>

@enduml

```



#### Listsprites

Add the listsprites keyword



![](/StdlibUnderTheHood/3.3.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/all.puml>

listsprites

@enduml

```



### Where did that guy come from?

If any color is added we get an actor (from Deployment Diagram so can
explicitly use a rectangle as the Deployment Diagram entity - see next
example)



![](/StdlibUnderTheHood/4.png)




```
@startuml 


sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}

"<color:red><$Batch></color>"

@enduml

```



#### Lose the guy - add a Deployment Diagram Rectangle Instead



![](/StdlibUnderTheHood/4.1.png)




```
@startuml

sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}

rectangle "<$Batch>"

@enduml

```



### Add some color



![](/StdlibUnderTheHood/5.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>

rectangle "<$Batch>" 

'this overides/specifies a color as red
rectangle "<color:red><$Batch></color>"
@enduml

```



### Understanding the AWSEntity Macro

Based on reconstructing the existing Macros, we can define our own
minimal macro:

    !define Batch(e_alias) AWSEntity(Batch, #D86613) as e_alias

where the parameters are

1.  `` `Batch ``\` this refers to the sprite \$Batch
2.  `` `e_alias ``\` this adds on a "as whatever" so multiple calls to
    same sprite return multiple rendered icons.
3.  `` `#D86613 ``\` is the color defined as part of the sprite puml
    file



![](/StdlibUnderTheHood/6.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>
!include <awslib/Compute/Compute.puml>



'Use the Compute icon here for contrast
'this uses a macro - and hardcodes the color - color copyNpasted from Batch.puml file
'===================================================================================
!define Compute(e_alias) rectangle "<color:#D86613><$Compute></color>"  
Compute(Compute) 
Compute(Compute) as something


' This uses the AWSEntity macros defined in Batch.puml
' the end result is same as above - but we use the e_alias so that multiple calls show
'===================================================================================
!definelong AWSEntity(e_sprite, e_color)
rectangle "<color:e_color><$e_sprite></color>" 
!enddefinelong

' Batch.puml
!define Batch(e_alias) AWSEntity(Batch, #D86613) as e_alias

Batch(whatever)
Batch(whateverElse) 
Batch(3.13xyz) 


@enduml

```



#### Add Scaling to AWSEntity Macro

Replacing the last lines from the previous example to add scale.



![](/StdlibUnderTheHood/6.1.png)




```
@startuml 

!include <awslib/AWSCommon>
!include <awslib/Compute/Batch.puml>
!include <awslib/Compute/Compute.puml>


'Use the Compute icon here for contrast
'this uses a macro - and hardcodes the color - color copyNpasted from Batch.puml file
'===================================================================================
!define Compute(e_alias) rectangle "<color:#D86613><$Compute></color>"  
Compute(Compute) 
Compute(Compute) as something


' This uses the AWSEntity macros defined in Batch.puml
' the end result is same as above - but we use the e_alias so that multiple calls show
'===================================================================================
!definelong AWSEntity(e_sprite, e_color)
rectangle "<color:e_color><$e_sprite></color>" 
!enddefinelong

' Batch.puml
!define Batch(e_alias, scale) AWSEntity(Batch*scale, #D86613) as e_alias
Batch(whatever,2)
Batch(whateverElse,5) 
Batch(3.13xyz, 0.3) 


@enduml

```




This scale parameter could be added to existing macros in puml files
e.g.
<https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/Compute/Batch.puml>

But, for each macro (4 in this case), we would need to add a new macro
that supports a scale parameter (giving 8 macros in total).

This is not very extensible or future proof!

So we need to come up with a better way...



    !define Batch(e_alias, e_label, e_techn) AWSEntity(e_alias, e_label, e_techn, #D86613, Batch, Batch)
    !define Batch(e_alias, e_label, e_techn, e_descr) AWSEntity(e_alias, e_label, e_techn, e_descr, #D86613, Batch, Batch)
    !define BatchParticipant(p_alias, p_label, p_techn) AWSParticipant(p_alias, p_label, p_techn, #D86613, Batch, Batch)
    !define BatchParticipant(p_alias, p_label, p_techn, p_descr) AWSParticipant(p_alias, p_label, p_techn, p_descr, #D86613, Batch, Batch)

### Updating the puml files to support minimal macro

Using AWSSimplified.puml as a reference, we can create an AWSBare.puml
file.

    ' Styling
    ' ##################################

    hide stereotype

    !definelong AWSEntityColoring(e_stereo)
    skinparam rectangle<<e_stereo>> {
        BackgroundColor AWS_BG_COLOR
        BorderColor transparent
        Shadowing false
    }
    !enddefinelong

    ' Overwriting Elements
    ' ##################################

    !definelong AWSEntity(e_sprite, e_color)
    rectangle "<color:e_color><$e_sprite></color>" 
    !enddefinelong

For each icon puml file e.g. Batch.puml

:

    !define Batch(e_sprite) AWSEntity(e_sprite, #D86613)
