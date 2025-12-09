# Google Cloud Platform‎

> In this section we'll look at a Google Cloud Platform‎ icon set
> <https://github.com/Crashedmind/PlantUML-icons-GCP>.
>
> PlantUML will access it directly from this repository (It is not part
> of PlantUML Stdlib.)
>
> This a Type 2 PlantUML stdlib per `PlantUML Stdlib Overview`:
>
> The original icon set is from <https://cloud.google.com/icons> (which
> says "*We are currently in the process of updating our product icon
> set*.")

------------------------------------------------------------------------

## Original

This diagram is from
<https://cloud.google.com/blog/products/gcp/brick-by-brick-learn-gcp-by-setting-up-a-minecraft-server>

## PlantUML Equivalent



![](/Using%20standard%20library/gcp/gcp4.png)

The icons could be put into coloured boxes as shown in
`Create Real Life AWS Diagrams`



## Find icons

We can see all the GCP icons here:
<https://github.com/Crashedmind/PlantUML-icons-GCP/blob/master/Symbols.md>.



![](/Using%20standard%20library/gcp/gcp1.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton_gcp1" />](http://www.plantuml.com/plantuml/uml/VO_1QWCn34Jl_eha0xAwzvIoXH98O2yzByfQNGjisLWo_VqA2iqXa9COyMQaEQjXjr5oE4RwPg73vxmihW_9hEaRGCUVQMTBupwK-bR5I6pQQe6veoQAXIN2ab7iwtOziHDwyX0eg4OT8gk58ykMH_nF1vzpBQNAr5o6P-3zigB4zOPRyg_MAs4NbXqmvp_BisEvE2wuKo6n5w0VRiFe1V61XdTKqWSJilVGrjb8mvaa-l8N)
Press to play around with this diagram source online.

### Source


```
@startuml
!define GCPPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-icons-GCP/master/dist
!include GCPPuml/GCPCommon.puml

!include GCPPuml/AI_and_Machine_Learning/all.puml
!include GCPPuml/API_Management/all.puml
!include GCPPuml/Compute/all.puml
!include GCPPuml/Databases/all.puml

listsprites
@enduml
```

## Gather the icons we need

In addition to the GCP icons, we need:

- users, clients, mobile icons; we can use the awslib for these

- timer: we can use material stdlib for these

  > - I used `GitHub File Finder` to search for "timer"



![](/Using%20standard%20library/gcp/gcp2.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton_gcp2" />](http://www.plantuml.com/plantuml/uml/fPDHRnCn3CVVyocylkoGkkPzGcZZn7Y0GaMPUApIYzjQooMdnCTzVTnatTfnPI0gzLmxV__g_EMxIMmYzwrJ5nOtv14-rek5vB1ZxjArrj4Ciotnhb_t2MCJFAFdMHDQNKUJTcXRybOldF5yF_zyHQ98LmBHhKcCKLjAh2x8DwwtJtGjiGvj6_oia_JtSpdiUaPTkz3RrLtl6oO1dr5_GHv2V22_FJHGnC4uj_hMEqol_KU9gmz-InxFY9SSejaU1YhPerRfI_LzXn1uXn6o0J2GS-0HBN00CGjX4qFxA4bi7Qr1lj54mdGDQzCyzDqKzXQdAJIEq7EQgKlzFCbRCoHfqRS_biMwTwDdIsexHnj2cwSR4HtkBVwSaxHXJUwFYYrwZCOTIPIwtqzVvUSK9dUHqDiqaPymUQFc6LcL8BL3lSvthKgGsYUoeE7h8FXHoPmyDj5i-8YXNgn9zI9ViebxVOwmnFYpmBCCdcH2UXKKkZr7mdzWRgsLBdc2WUBIE4MTRcPrcahBN48jNfpSgOYWY3BbU6Mha-o4yJulONgUfOWoO-orgiQAg-mnnca6D-FWGmla5k7_FRxuzMzq-Tn8aspfBm00)
Press to play around with this diagram source online.

### Source


```
@startuml
!define GCPPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-icons-GCP/master/dist
!include GCPPuml/GCPCommon.puml
!include GCPPuml/Compute/Cloud_Functions.puml
!include GCPPuml/Networking/Cloud_Firewall_Rules.puml
!include GCPPuml/Compute/Compute_Engine.puml
!include GCPPuml/Storage/Cloud_Storage.puml

/'
The other icons will need to come from other stdlib libraries: backup, users, clients.
'/
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>


Users(Users, "Friends", " ")
Mobile(Mobile, "", " ")
Client(Client, "Kid / Owner", " ")
Client(ClientMinecraft, "", " ")

Cloud_Functions(Cloud_FunctionsStart, "Start Server", "Cloud Functions")
Cloud_Functions(Cloud_FunctionsStop, "Stop Server", "Cloud Functions")
Cloud_Functions(Cloud_FunctionAdd, "Add a Friend", "Cloud Functions")

Compute_Engine(Compute_Engine, "MineCraft Server", "Compute Engine")

Cloud_Storage(Cloud_Storage, "MineCraft Backups", "Cloud Storage")

Cloud_Firewall_Rules(Cloud_Firewall_Rules_Starter,"Minecraft Backups", "Cloud Firewall Rules")
Cloud_Firewall_Rules(Cloud_Firewall_Rules_Friend,"Minecraft Backups", "Cloud Firewall Rules")
@enduml
```



## Connect The Icons



![](/Using%20standard%20library/gcp/gcp4.png)



In this case, we took an icon from a different stdlib library (material)
and wrapped it in our template so it looks consistent with the other
icons.

> We can take a sprite from any sprite library and apply a selected
> library styling.
>
> In this case, we took a sprite "ma_timer" from a different stdlib
> (material).
>
> We used the macros from the GCP library to color and style the icon to
> match other GCP icons.
>
> - EntityColoring("Backup")
> - Entity("Backup", "Backup","Cron Task", "darkgrey", "ma_timer",
>   "Backup")
>
> These macros can be found in
> <https://github.com/Crashedmind/PlantUML-icons-GCP/blob/master/source/GCPCommon.puml>
>
> "ma_timer" is not a Google service so we don't colour it blue.
>
> Alternatively, we could write the style at a lower level but that's
> more work e.g.
>
> 'rectangle "==Backupn MA_TIMER(darkgreen)n//\<size:12\>\[Cron
> Task\]\</size\>// " as Backup

### Play

[<img src="../res/play.png" width="40" alt="playbutton_gcp4" />](http://www.plantuml.com/plantuml/uml/fLLHRzis47xNhxZg9IfWXzWUWzHe9ZJ3i7aBwXHzQ0k35Yyo5ueKI6f6DlI_xqH6TcHJHeOPi2Zolhll-1rFVEyyjxvhLFP6u8FK23-NTtSqXwtthRjYpFBTPItzjjjq3crbj4VjBolJiD9ojqNHI2tOdUBQVrh-DfU4S7CAmXhkF5ecfFFP6wahrObzT4PZQPh6wCkMfgTsChQTHrOgqudrRQShBodm1Fftz3jZ7wMk1mTfSSULMd_i5Bhp7CEu_g1h4c02lFB6ydf8ACwUiHcxoEwt2CPlqK8G07PIAT280hm14WlXmPhc6UAyK783zBVSIdHNiE7LOzVEe9VOpQ1IaaHsbza5EsHopNUENDZDvrMKRf6qhMJJAlaWKOJi4g1XtwJF5AGn6wdE8chKQBbw0Nc1QRX7AybQnKHJ9YyRj8FhXQFYjTpoXbJHw9zQXDQeftwIGS9ehDyQylEcxHNU6Ez9NY4jXeC2MKkAKeKW_rKAOF37ZjBDuPyCwFUfLxa8pndajvR45YwdLyZV1a0Pz2_YC1l5663VimF5ahAgB7_mqS4HpscOFOW2lEHQ1gcBE4JRD07SMVCdRR5d2DxUr1ZEL6GyQfVYQBxotFRyOOGLsh_YXW8CzZ1YVrKmqv9lF_pFK3T2a2SzWKEindIax-4vRjbYF9r5mKeIRBJ92888ed0XqgYVYz5i5EUdqA7ka5W4KPna8LAVeIArk0wrG3lBdr_WzZEbwAt45sI33mGVulnl757KMHx7rpD4iSFZOhWFubtmcWjWeynck0MSwMo5Hv_z6BXlMQvhXG3vktTHvwyQbZVh-r-M7puMWjl7sYBgjryrOzTE_erNF_ou-59Qe-6UkyTlrwnVN306EN07CSGXTTghz4-bKSPANHTvjDCM3yRzuWpsR_cUe5zzpkAfVs_uEdoz3kZOh_HBDHpClsob4AY_YVa24bsK9TREEL6dJ355yFGnoquYHPypnoOxOqjccIQUI7XnrCifBHAeyJJkOTIyiHYK8t5OCgROpmEeBk6A87Ew0jdHXpq2pocPnTC2y-vqH-y9G3tnBm00)
Press to play around with this diagram source online.

### Source

```
@startuml
!define GCPPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-icons-GCP/master/dist
!include GCPPuml/GCPCommon.puml
!include GCPPuml/Compute/Cloud_Functions.puml
!include GCPPuml/Networking/Cloud_Firewall_Rules.puml
!include GCPPuml/Compute/Compute_Engine.puml
!include GCPPuml/Storage/Cloud_Storage.puml

/'
The other icons will need to come from other stdlib libraries: backup, users, clients.
'/
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

!include <material/common>
!include <material/timer.puml>

'skinparam linetype polyline
 skinparam linetype ortho

'top to bottom direction 
package "Kid / Owner" {
    Users(Users, "Friends", " ")
    Client(Client, "Kid / Owner", " ")
}

package "MinecraftClients" {
    Client(ClientMinecraft, "", " ")
    Mobile(Mobile, "", " ")
}

package "Minecraft Project" {

    together {
    Cloud_Functions(Cloud_FunctionsStart, "Start Server", "Cloud Functions")
    Cloud_Functions(Cloud_FunctionsStop, "Stop Server", "Cloud Functions")
    Cloud_Functions(Cloud_FunctionAdd, "Add a Friend", "Cloud Functions")
    }
    Compute_Engine(Compute_Engine, "MineCraft Server", "Compute Engine")

    Cloud_Storage(Cloud_Storage, "MineCraft Backups", "Cloud Storage")

    together {
    Cloud_Firewall_Rules(Cloud_Firewall_Rules_Starter,"Starter FW Entries", "Cloud Firewall Rules")
    Cloud_Firewall_Rules(Cloud_Firewall_Rules_Friend,"Friend FW Entries", "Cloud Firewall Rules")
    }
    
    'https://github.com/Crashedmind/PlantUML-icons-GCP/blob/master/source/GCPCommon.puml
    'rectangle  "==Backup\n MA_TIMER(darkgreen)\n//<size:12>[Cron Task]</size>// " as Backup
    
    EntityColoring("Backup")
    Entity("Backup", "Backup","Cron Task", "darkgrey", "ma_timer", "Backup")
}




Cloud_FunctionsStart -[hidden]d-> Cloud_FunctionsStop
Cloud_FunctionsStop -[hidden]d-> Cloud_FunctionAdd

Cloud_FunctionsStart -d-> Cloud_Firewall_Rules_Starter
Cloud_FunctionAdd -d-> Cloud_Firewall_Rules_Friend
Cloud_Firewall_Rules_Friend -[hidden]d-> Cloud_Firewall_Rules_Starter

Cloud_FunctionsStart -> Compute_Engine
Cloud_FunctionsStop -> Compute_Engine
Compute_Engine -d-> Cloud_Storage



Client -r-> Cloud_FunctionsStart
Client -r-> Cloud_FunctionsStop
Users -r-> Cloud_FunctionAdd


ClientMinecraft -r-> Cloud_Firewall_Rules_Friend

Backup -u-> Compute_Engine
@enduml
```


