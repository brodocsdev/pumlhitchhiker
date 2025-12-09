# Create a Diagram of a Typical Network

> In this section we're going to create a full network diagram by
> walking through it step by step.
>
> Each step has
>
> 1.  An objective - the step heading
> 2.  Source code - for the diagram
> 3.  Play - where you can test the diagram and play with it.
> 4.  Explore - where you can confirm your understanding by trying
>     things as you play.

## Example Network Diagram

[<img src="../res/play.png" width="40" alt="playbutton0" />](http://www.plantuml.com/plantuml/uml/VLNlQkGs4F-kfvWB77NWuetthd-Q3-NI59h0fLt8XdufB8eqNelOaf7acAKK-XfzlJv9PoHxDybo-M2FD7z-C_ERyUxd4AMFGzSAyKvZRIo22t952cXYxCF5Ok7bM6vDR8Q78Q1NpaQqiLIkMrnv6HhKdR5wiMgbZVUtNyvSZpQW6ho9E-bLOoAgE7XSdXcA3OjEXeXUl3DMjOFUfrjSkQvpjkpfV6oyfymBsRPVCLzBhqVfyGsNMnFK6-Oxz4zlfhWpyHcy-AQ4M-btO098-0MViAM-FHWBiK5OUQS75I6Yx4gu8qqZsV4FOigD0QfpM5s1j9eUkBJQEwEXRvp5af5_TWyP-5PQkJt0NYhb1Xl3X7kTOCb9pL1cjSUuUU9xOEtD6hR33iR6GUlS8-dgY3uXXjHs2HonRd07D2ABNBbBTejnTFuHQFWVKf8d8q52RJoEHCRiTcC9a7nBGSm03ok8wBP8DWz_2U9mmxkpsNf4kz4pNGLJ-05EM9oGV4uRt_Uydfo-nc2jZCRPK72dvCo2WwZRzHIVXmgNlA774BJEnc88cowpN13j54HlZdt1DIkcMH3EtzmarMOK7hMfCJn6rnUzef3gnsLPVVT3MPNLEKCSnf-wlPfgQcNF8Pry5RFCQTKiidUUSM5w5apIpihEABXPiL-sGbNn9PrVXicyR4Tnqn9IQQy3yueKMRngAZdVFn1F0qnaBy_Byq_mPNrt642cZ3ZxBM-Jc9XY0ZUZyTZo5BmR8kKPJMqkLo_pCDGKEnL5-rZGG_hVwvfWW2xiTKqYUymhMim7idvRbH-_BvUVgFAFnvYgTOCkqfjiyqg_z1CYVVLdPpz1houWkC5JSkKq7WmJnMnLHhRGeJPI2DghPEua1TR6IfkinjPkRyj3lO0aG57LWLBoPYTpdi45VwIrsGxv0n0YHoMFp9wOIdYkoe8rp9KG6Mj_fwhsv_vm58BUwJRJACHyIkf45-cSYuJslZOjqbfXSGeUhKQFcWg83Sn_3q190rKDxwT3SVgdNJS8roQgfZ6FwF_xvzy0lmv68qIt3nIV2I_zz0hnFm00)
Press to play around with this diagram source online.




![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines7.png)




Here we have a typical network diagram:

1.  Mary is a Developer in the Product team. She has a Windows 10 PC and
    an Android phone.
2.  Bob is an Accountant in the Accounts team. He has a Mac and an
    iPhone.
3.  They connect to the office server, and via a firewall to the
    Internet.

There are 3 types of element with different properties:

1.  Users: Role, Name, Team
2.  Machines: Type, IP address, OS
3.  Network Equipment: Type, IP address, and e.g. product model and
    number

## Select an icon library

The OpenSecurityArchitecture library has a nice set of users and network
components so we'll use that.

> To see all stdlib icon libraries, browse to
> <https://github.com/plantuml/plantuml-stdlib>

## View all the icons with [listsprites](https://plantuml.com/#)

1.  Create a blank diagram that includes the icon files we're interested
    in

2.  Add a "[listsprites](https://plantuml.com/#)" statement

    > [listsprites](https://plantuml.com/#) lists all the sprites in the
    > files you include in your diagram source


caption="*Using listsprites to show all icons in a library*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines1.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton1" />](http://www.plantuml.com/plantuml/uml/VP2nQdCn38LtFuKp198XCVpZFmKoD4C3WJHR5zVMhKLj-IB9lNJhQ_Jr-YHreKs7qhiTpgV31zg9UjPMiZ6B20CIs2h-r0kRL4VvxnpxQVk8cjf34-1GIO5q6sfnU_QI81Qaw4xParwEjviw0Wc4ngWldaD2XQ2DuTy6-rPSyQB0Pe4KSejNdTlNKYfjnvv_mqitEv_p7_ZWEKwUOURaY19cy1duULPnHeKVR3AAoiYz56E6MXNOBWVCGBx0QcqPA093j1Dgij_FiTqXMCakly9gVKzt2Um1DQI4Jy3lhszYRnfsjTRhqEo0ugVu0m00)
Press to play around with this diagram source online.

### Source



```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

listsprites

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml

```



### Explore

1.  Take a look at some other stdlib libraries e.g.
    [awslib](http://www.plantuml.com/plantuml/uml/ROqnoi9044RxFSNyHI1f_bn096AXXOAWOcEpIIRiuEnks9qrhTVmUfx4BKG4xGQ-z-OrKNIGP5dzaUiuzGWpFKMcjbwSzajlhNVpxoqFOnAiDVF_cEqVYFKjyIUXcAB4CP1WL6hmNZ10CMJ8QOjb1G5TZm5xc4WCx5WxEMutSCKGoJieNaTPdTt18An9EcFeWk5nkqTO9SfryMzHDVbVBZy1)
2.  What happens if we don't include any libraries?

## Gather the icons we need

1.  Create a diagram with the selected icons

2.  This allows us to see and review the icons first with the icon name

3.  It also confirms everything is working before we connect them
    together.

    > We're using a Blue theme, so our icons appear blue by default.
    > Yours may appear yellow.


caption="*Select the subset of icons for our diagram*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines2.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton2" />](http://www.plantuml.com/plantuml/uml/VPB1Qjmm48RlVWe56feS4aEFeOH02isXAGjjRWMZIl-kXvL7PZIowQslqTVharIki0iDkmV3_FFDx_b1yv3KYkOXDCs5nvuO9YQxAmtJguxfhct5phS7qZv_pmdY8YjORrqSsaUngOSVY7sx2vRrvVdJJHp12IuBwGyhhYU5qonuTqF5czh19eKq5yGkPB-jQn_ZC4I-7Klz6huaI6j3E86VhFZP2iwCF5DoP_0No0GvDq2AVxXvQvP8gIcuowNg3W9mvp4Xn15oPzw_ESNk_tSjJQiKELNR2VZALnw462brWsLxM9UU7RbVed_0H0url4SwQXohTPDrLR3ZYghQ2EtwoAXaLPKao5IJRAek_GoTenphqhy1kfa4OGadCMirdQRrz-KArx5IrjwU1BCDOGMhhdJvN8ZPBtWJ9T8-HeMOopq5i1rmTMq4x27mPYRjpNhIPe8aYcmkQy5Nrz_uQm_pHEhwdewGtpz_9VCnauVHk1cR1x1VpkKF)
Press to play around with this diagram source online.

### Source

> We can't have the icon on its own e.g.
> "\<\$osa_user_green_developer\>" would not work


```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

' Users
osa_user_green_developer: <$osa_user_green_developer>
osa_user_green_operations: <$osa_user_green_operations>
osa_user_green_business_manager: <$osa_user_green_business_manager>

' Devices
osa_desktop: <$osa_desktop>
osa_laptop: <$osa_laptop>
osa_iPhone: <$osa_iPhone>
osa_server: <$osa_server>

' Network
osa_device_wireless_router: <$osa_device_wireless_router>
osa_hub: <$osa_hub>
osa_firewall: <$osa_firewall>
osa_osa_cloud: <$osa_cloud>

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml

```



### Explore

1.  Change the server type to a different type of server
2.  Change the Operations user type to a different type of user

## Decorate the Icons

1.  We use the default functions defined as part of stdlib that decorate
    our raw sprites
2.  This makes them much more visually appealing.


caption="*Decorate the icons for our diagram*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines3.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton3" />](http://www.plantuml.com/plantuml/uml/XPF1QXin54NtynMA8LI6nWDTTXL8eLaqnT1cLp2AT6qzh966fwSPkkjlzFVw9PM9uuGsSbO-ddCbtSTehhCObZA4hhjms5A4IjciwmFbHSRyiU_PpAiTYIyF9ODjYe8eAvk6_ePDzd03HTUlWuboV_VbAes86ROmoK_3rfF0Ic5ykAAwDlU3oGBkBYZQKDpfkFuc3KEAgx7o__8-WtiJGaFV6dQpOPo9t56sP_Gty0G-5o31i-wwT-hGANVLRqgbpOw1k76O4D88rYtnNYs2UK1OL11OlrZ-kySXPOHIpBfftjwblYsAo7apc6XsO7tUlzQh3la94rayZkcGzv96_O8RDO8Pdu8LspbQ-nIXdx6Ho-09h4_OAFiLCYVU7yiUYczcOeJ3b9oAW7LRDOwkrruVVnk9BJ5c4u9--QUHjI4Lfq_qsXZRb0IiBhSK4Cq0lLICwC1mQYRnwkbBKnCuKuhgyWXw-ID-zr2t9DPxseF__FgTrUT23ahIQM5tZUWUR_5V)
Press to play around with this diagram source online.

### Source


```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

' Users
osa_user_green_developer: <$osa_user_green_developer>
osa_user_green_operations: <$osa_user_green_operations>
osa_user_green_business_manager: <$osa_user_green_business_manager>

' Devices
osa_desktop: <$osa_desktop>
osa_laptop: <$osa_laptop>
osa_iPhone: <$osa_iPhone>
osa_server: <$osa_server>

' Network
osa_device_wireless_router: <$osa_device_wireless_router>
osa_hub: <$osa_hub>
osa_firewall: <$osa_firewall>
osa_osa_cloud: <$osa_cloud>

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml

```



## Create the diagram by connecting things together

Now for the fun bit...

1.  Mary is a Developer in the Product team. She has a Windows 10 PC and
    an Android phone.
2.  Bob is an Accountant in the Accounts team. He has a Mac and an
    iPhone.
3.  They connect to the office server, and via a firewall to the
    Internet.

 caption="*Connect the icons*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines4.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton4" />](http://www.plantuml.com/plantuml/uml/VLJTRkis3BxNK_0KE9WBd3fnpjdFUZ6ShWFM0iqMe2bsCo1G9JeMQak69DV8tLvZhxSd6MbPMTjW3H2H8lbzb3uH_XgYz77eMY4-QAoDHN11RYW0JOnzk5mil1pBlOdDy3W4zChPY3QModMBQoz3WxepLYyshRJnONrtuNgq0TNWJJn8hneJKSN1u-h243OiEXaYUl71MDKE-jXkSUswpjco9_yq-K2T5x9j_oTz8xqUfSTtIjOcg7VIz-YVtsrnR-8BUl5D2Mlf3s02IFW5dx6bUtim5cA3iF5E3of2HDcLS4-HHdBX7wIK6mDKIzXSWxIQ_d1bjNT6GzyuYoKp_-mU4_5QMhd_Z_PAAJVO66RUcqIxbYfJcSsHu_QPzu6ZjrlO3mSO6mUjSqyKgoFwYJ5Crow14Ti63w2SjSWdTrFUOXoTVm9w_4zJasSZGK9jF8uaHYwxjKH8jQKWPO0VAmWIRiS3izjxHBlJMQE2TVi4PspEoBxKYlT7CS_Ett9mL4RZR2ZuUbJCXa5qnUsCJoy9LpoMfnGqmyPY2BikILkGrWIYbR6l1ER0_034G_UYanc5wMOQmrDqVT4hggf-N9NLTp-KLLaj6PMVEUqsr_CnMjapf9DlCAlKIMMJgjDR5gPdmxeShEoCWjiDrwKiL1Ll9lyrJAQXEi7bOQkMRu5f58fatbngAdvu96a6cFLTBSlb5xZRtcVDiqg_fP6PLMB5TgFnsBBetWsHUeocDbURrpsOPeRE1wAPA-XFyT_hccY0DbnrGoPLv34iiaFPRwloy_VbwWkT-lCffshTe8jffLmUszTrWYSJBdw2Nbr2S8EdriffFCPdRJcfZ6oXGssa43H3dEqamMfZfPsInjOkfz9RNi9aGD61Wn0ymfnCmbzIArkR_P06NOY4uOAacfYxluY8P2d24eb4b7TqdEpsHq_GmdxMJOZiSNIIXqBEHUBvM9iMQOImE0UFLgD7JPrZ0_cJ3zGk66VXu-mKvt_QRODmOw9g6lE4_f-__Wxmws0qGdH7eFXAVFmvfT-_)
Press to play around with this diagram source online.

### Explore

1.  Add some text to describe the connection from firewall to cloud

### Source


```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

'. Mary is a Developer in the Product team. She has a Windows 10 PC and an Android phone.
'. Bob is a Manager in the Accounts team. He has Mac and an iPhone.
'. Ivan is an IT guy who looks after the server. 
'. They connect to the network hub, and via a firewall to the Internet.


' Users
osa_user_green_developer(Mary, "Mary", "Product team", "Developer")
osa_user_green_operations(Ivan, "Ivan", "IT Team", "Server Admin")
osa_user_green_business_manager(Bob, "Bob", "Accounts team", "Manager")

' Devices
osa_desktop(pc, "192.168.1.10", "Windows 10", "PC")
osa_laptop(mac, "192.168.1.12", "Mac", "Mac")
osa_iPhone(iphone, "Dynamic IP", "iPhone 11", "Phone")
osa_iPhone(android, "Dynamic IP", "Android 10", "Phone")
osa_server(server, "192.168.1.100", "Ubuntu Server 20.04 LTS", "Server")

' Network
osa_device_wireless_router(wifiAP, "192.168.1.1", "Network")
osa_hub(hub, "Office hub", "Hub")
osa_firewall(firewall, "51.37.24.103", "Network")
osa_cloud(cloud, "Internet", "Network")

Mary -> pc: source code
Mary -> android: social media

Bob -> mac: financial info
Bob -> iphone: phone calls

Ivan -> server: configuration

iphone -> wifiAP
android -> wifiAP

wifiAP -> hub
server -> hub
mac -> hub
pc -> hub

hub -> firewall

firewall -> cloud

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml




```



## Change the Layout to Vertical

We want the diagram to be vertical, with the cloud at the bottom and the
users at the top.

> We use `-->` to connect the icons so they are arranged vertically.
>
> See `Layout` for more info on arrows and layout.

 caption="*Vertical Layout*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines5.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton5" />](http://www.plantuml.com/plantuml/uml/VLNDRYCt3BxhARW15fq0ct7itVuqXsBJ56W29As1EEYbWA5870-H6McWdnY-zJNwUdsIKjACdSJO73oaI7uVgKz4yjK7wKBiEo4-Q6p885Wlbno0DeJ1NyncJcxh3OKsFaQFJbaJq8HQsNvsvQHlKVTaz6pPIHCUxcxFx836eugEmauwrL905QB3nHanrizwwGCwyO6CwgBUjvjTsRwtfXxOFqu-SEUPxBflfA-bqrlfy9sIE_BgdVGzkkTtMznJU44llglXJheTa0S9l-4pTdnl1sGWj0XBPtLK0GBAlePxZhGo5Vx5IjcjX_avBAz06iq_k3JQMT8mjDPWdPX_jO-5-4uQkJdGNYfbemb-vBtEj5oa9YfQxZbkdjFPf-ZD2ZPn1zlMGcVj4yUQW2up-dpj6X9YrU8Eb3K6q-Gsvms6hNLFm8__AJTv9WaI6dAuPJ6ciXl3X5nR2rO6qcDv8LYvTMHtlN68PgqdaQeat2SuIUQ4xKknqdclvidfMuuKbO6iyLMw7nSdaq1ynzM8Bqy9bsalZobuYScWz-k-Q5kns0pYRyA-KZW5nXTW7huOJqOAVQRKw9-27Qf1STNyvqKz_-6dUbxFpnFgyCxvWbVZ69qS4gINRp2BqabDfbINnwneI2RfiZEo9mKtorHNiZ2VfqFsNyDasQeZtBXjFDfRODc5gfWtbyh53uyiJOHHtyLvVVu5RbVt1ysBId-KdIagPSNMMtBO9T6TZO5xRAcXo-Nh7ebcX8u3yT9L_EFudqt3DC27L7NDfbHCUrXD3cU_dzUVVwmNNtZgpyUSghDHL_dBkMblNzS9aLOJpiv-WK5TWBVHSNDbDHuIexmfgqXsqACcAGIlKKxtae4D6MbobanZzxdoe1UG3IYUsdFBjCWvNVI_u7wceKqi-ov4GUMAefuOHtWPAYP7M2iX2jV-p5Fj_U7W2i7VV9fa56BoSZZBnJ5h0xDzRAX3NYciJi6XqUXGym2XXUb_071JprF3nz6fJlysgnRXce9gMtf2zzy__thuFP9627OF55-PB_zz5U9_)
Press to play around with this diagram source online.

### Explore

1.  Arrange the diagram vertically with cloud on top, users on bottom
2.  Arrange the diagram horizontally from left to right with users on
    left, cloud on right

### Source



```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

'. Mary is a Developer in the Product team. She has a Windows 10 PC and an Android phone.
'. Bob is a Manager in the Accounts team. He has Mac and an iPhone.
'. Ivan is an IT guy who looks after the server. 
'. They connect to the network hub, and via a firewall to the Internet.


' Users

osa_user_green_developer(Mary, "Mary", "Product team", "Developer")
osa_user_green_operations(Ivan, "Ivan", "IT Team", "Server Admin")
osa_user_green_business_manager(Bob, "Bob", "Accounts team", "Manager")

' Devices
osa_desktop(pc, "192.168.1.10", "Windows 10", "PC")
osa_laptop(mac, "192.168.1.12", "Mac", "Mac")
osa_iPhone(iphone, "Dynamic IP", "iPhone 11", "Phone")
osa_iPhone(android, "Dynamic IP", "Android 10", "Phone")
osa_server(server, "192.168.1.100", "Ubuntu Server 20.04 LTS", "Server")

' Network
osa_device_wireless_router(wifiAP, "192.168.1.1", "Network")
osa_hub(hub, "Office hub", "Hub")
osa_firewall(firewall, "51.37.24.103", "Network")
osa_cloud(cloud, "Internet", "Network")


Mary --> pc: source code
Mary --> android: social media

Bob --> mac: financial info
Bob --> iphone: phone calls


Ivan --> server: configuration

iphone --> wifiAP
android --> wifiAP
wifiAP --> hub

server --> hub
mac --> hub
pc --> hub


hub --> firewall

firewall --> cloud

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml




```



## Change the Layout by grouping icons [together](https://forum.plantuml.net/4387/please-provide-together-keyword-group-diagram-nodes-together)

Here we use the `together` keyword.

> The `together` keyword allows you to specify what icons you want to
> group together. Like all layout options, minimize their use. See why
> in the Explore section.

 caption="*Group our icons*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines6.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton6" />](http://www.plantuml.com/plantuml/uml/VLNlQkGs4F-kfvWB77NWuetthd-Q3-NI59h0fLt8XdufB8eqNelOaf7acAKK-XfzlJv9PoHxDybo-M2FD7z-C_ERyUxd4AMFGzSAyKvZRIo22t952cXYxCF5Ok7bM6vDR8Q78Q1NpaQqiLIkMrnv6HhKdR5wiMgbZVUtNyvSZpQW6ho9E-bLOoAgE7XSdXcA3OjEXeXUl3DMjOFUfrjSkQvpjkpfV6oyfymBsRPVCLzBhqVfyGsNMnFK6-Oxz4zlfhWpyHcy-AQ4M-btO098-0MViAM-FHWBiK5OUQS75I6Yx4gu8qqZsV4FOigD0QfpM5s1j9eUkBJQEwEXRvp5af5_TWyP-5PQkJt0NYhb1Xl3X7kTOCb9pL1cjSUuUU9xOEtD6hR33iR6GUlS8-dgY3uXXjHs2HonRd07D2ABNBbBTejnTFuHQFWVKf8d8q52RJoEHCRiTcC9a7nBGSm03ok8wBP8DWz_2U9mmxkpsNf4kz4pNGLJ-05EM9oGV4uRt_Uydfo-nc2jZCRPK72dvCo2WwZRzHIVXmgNlA774BJEnc88cowpN13j54HlZdt1DIkcMH3EtzmarMOK7hMfCJn6rnUzef3gnsLPVVT3MPNLEKCSnf-wlPfgQcNF8Pry5RFCQTKiidUUSM5w5apIpihEABXPiL-sGbNn9PrVXicyR4Tnqn9IQQy3yueKMRngAZdVFn1F0qnaBy_Byq_mPNrt642cZ3ZxBM-Jc9XY0ZUZyTZo5BmR8kKPJMqkLo_pCDGKEnL5-rZGG_hVwvfWW2xiTKqYUymhMim7idvRbH-_BvUVgFAFnvYgTOCkqfjiyqg_z1CYVVLdPpz1houWkC5JSkKq7WmJnMnLHhRGeJPI2DghPEua1TR6IfkinjPkRyj3lO0aG57LWLBoPYTpdi45VwIrsGxv0n0YHoMFp9wOIdYkoe8rp9KG6Mj_fwhsv_vm58BUwJRJACHyIkf45-cSYuJslZOjqbfXSGeUhKQFcWg83Sn_3q190rKDxwT3SVgdNJS8roQgfZ6FwF_xvzy0lmv68qIt3nIV2I_zz0hnFm00)
Press to play around with this diagram source online.

### Explore

1.  What happens if we put a "together" around the network elements
    too - line 33?

### Source


```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

'. Mary is a Developer in the Product team. She has a Windows 10 PC and an Android phone.
'. Bob is a Manager in the Accounts team. He has Mac and an iPhone.
'. Ivan is an IT guy who looks after the server. 
'. They connect to the network hub, and via a firewall to the Internet.


' Users
together {
osa_user_green_developer(Mary, "Mary", "Product team", "Developer")
osa_user_green_operations(Ivan, "Ivan", "IT Team", "Server Admin")
osa_user_green_business_manager(Bob, "Bob", "Accounts team", "Manager")
}

' Devices
together {
osa_desktop(pc, "192.168.1.10", "Windows 10", "PC")
osa_laptop(mac, "192.168.1.12", "Mac", "Mac")
osa_iPhone(iphone, "Dynamic IP", "iPhone 11", "Phone")
osa_iPhone(android, "Dynamic IP", "Android 10", "Phone")
osa_server(server, "192.168.1.100", "Ubuntu Server 20.04 LTS", "Server")
}


' Network

osa_device_wireless_router(wifiAP, "192.168.1.1", "Network")
osa_hub(hub, "Office hub", "Hub")
osa_firewall(firewall, "51.37.24.103", "Network")
osa_cloud(cloud, "Internet", "Network")


Mary --> pc: source code
Mary --> android: social media

Bob --> mac: financial info
Bob --> iphone: phone calls


Ivan --> server: configuration

iphone --> wifiAP
android --> wifiAP
wifiAP --> hub

server --> hub
mac --> hub
pc --> hub


hub --> firewall

firewall --> cloud

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml




```



## Add a Legend Table and a Note

We add a note ala "note left : Look at Bob" where the note instruction
is on the line following Bob (the icon we want to put the note on).

A diagram Legend can be useful.

This example shows

- how to create a table

- how to add <https://plantuml.com/openiconic> sprites

- how to add stdlib sprites and scale (\*.4 in this example) and colour
  them.

- how to change the table cell colour

  > openiconic sprites are referenced with a "**&**" e.g. "&box"
  >
  > stdlib sprites are referenced with a "**\$**" e.g.
  > "\$osa_user_green_operations"

 caption="*Add a Legend*">

![](/Using%20standard%20library/NetworkUsersMachines/NetworkUsersMachines7.png)



### Play

[<img src="../res/play.png" width="40" alt="playbutton7" />](http://www.plantuml.com/plantuml/uml/ZLRTRkCs4xtdKypc-xRh51ivpgO_DLnZqmJO14YwHkEWDmK2cXnPX2LI8AbutMQ1laPVhq_I6Kgs4mS98a3YpyoSEJmp9lmnHEbZKvL2lD6O6ulWWfpG1XGnrc7OxtkvpEOc5isi2UYLin5jp9Ih-gTUXW9rPQpkJqffuytLvO6hqGPKZJTn9RqgJ4GL6uz71uPYGx-I8Q8NRunLPQCtwVgdhggSpMgQFpNUKEQ-BCjdpEVIwwNq-8BBbGdg1VCr-ZlqBpcO-01UlClWIleLc00Ipl0EIpgt1sCX5WWJxtIZ8aIKLGRNj5D8TloTb7BB08D3c9o2j9fUEB7QEwEXBfp5Z95_SRCM-4fQET_2dYZb6Xj3XtkUOCb9hQ7CP8DnSSVhmBiNKvWtArWM3ahd5hINH_G9CQHZPy0Hqm9NG2MooCnTibkCI-SNGCL_dvBS6GaISkDnIMAitIui0P9l9kXv1roj8AAR8naz_2L8n5jkdjkvHxItUgrNZpLy3tiyxD7uK3TURuJTsz_5u5qPZREXnqSbPnuuY8uxxUBRgi89j-XJ2EfdOp64swgLkKUwKn1zENOhTWVM5ODmh8i89UOHXd19YeACN3FnbGzFd8t29yVN61RHrRrQ4TJWfwDiyFsFsI0R73BqjY-I2gSTrrBM75B9dPYZbexgXiwxBNxFr3omU2ihAwFWOi9-hHK60rwa-UCmsNRXaxYkEudQRc3RExrss3bKShwPaNuDT4KuEimEZ-5oUhqj305zJGtpQzjcebEA1RnT6eybLyUx9bAUfSdDoUHn7eRgOZjIrAWzUcd_SvuJ3D22lSvfQ3tMlTjRJyZwtI3xy4DsT4pCFpp5LALhT2zzoRRkzST-GgJhuE1W3BKQGd2Df-JAQTmQEedPgemieK9jf13KESbSIGhCZPKsMOtDtSRM5dK8QG15h0Ebv8vFvhO6GyfdSpDlsX-646rKycZL4ns5Xrljm3kibH0jrcPDh3RpUZiLWhvfjPPHYFKiRIUvoAt4ELejW9xxd-7KbSxpPBggaSSp3CgRcld2VUi5es3-nE5WC1xDf5eC__SRwd4ISVkC-cmQZ_hiEhvFMugnX-my-lzp5ywtsJ459SynPKge6gCqPSWolW9DQ6_U47LfPX1gRo8-o-nC-iKdpZ3cKhoAtpQ4M3vtfUtGJE1Rci_I-UobdUEOckPLL3ftul7olRZ3Xk1VGsRI-BfaCbzUHQPp7tqpSryUPZi1GdXG6GiaapNAqRij3rhTDPh8dOleuMrkIhIomju-U3AWHqqj7mjO_rC1QlF0VVUsc_Js_x3J0k7SH5KKPe7-tx__2V2fCHeXkasW-4Xu_2-0dly0)
Press to play around with this diagram source online.

### Explore

1.  Create a table for each device and color code it as static or
    dynamic IP.
2.  What happens if you add "skinparam handwritten true" after the
    include section?

### Source


```
@startuml

!define osaPuml https://raw.githubusercontent.com/Crashedmind/PlantUML-opensecurityarchitecture2-icons/master
!include osaPuml/Common.puml
!include osaPuml/User/all.puml
!include osaPuml/Hardware/all.puml
!include osaPuml/Misc/all.puml
!include osaPuml/Server/all.puml
!include osaPuml/Site/all.puml

'. Mary is a Developer in the Product team. She has a Windows 10 PC and an Android phone.
'. Bob is a Manager in the Accounts team. He has Mac and an iPhone.
'. Ivan is an IT guy who looks after the server. 
'. They connect to the network hub, and via a firewall to the Internet.



' Users
together {
osa_user_green_developer(Mary, "Mary", "Product team", "Developer")
osa_user_green_operations(Ivan, "Ivan", "IT Team", "Server Admin")
osa_user_green_business_manager(Bob, "Bob", "Accounts team", "Manager")
note left : Look at Bob
}

' Devices
together {
osa_desktop(pc, "192.168.1.10", "Windows 10", "PC")
osa_laptop(mac, "192.168.1.12", "Mac", "Mac")
osa_iPhone(iphone, "Dynamic IP", "iPhone 11", "Phone")
osa_iPhone(android, "Dynamic IP", "Android 10", "Phone")
osa_server(server, "192.168.1.100", "Ubuntu Server 20.04 LTS", "Server")
}


' Network

osa_device_wireless_router(wifiAP, "192.168.1.1", "Network")
osa_hub(hub, "Office hub", "Hub")
osa_firewall(firewall, "51.37.24.103", "Network")
osa_cloud(cloud, "Internet", "Network")


Mary --> pc: source code
Mary --> android: social media

Bob --> mac: financial info
Bob --> iphone: phone calls


Ivan --> server: configuration

iphone --> wifiAP
android --> wifiAP
wifiAP --> hub

server --> hub
mac --> hub
pc --> hub


hub --> firewall

firewall --> cloud


legend
    |= Color |= Type |= Description |
    | <size:11><back:#Red>Mary           </back></size>|    <color:Red><$osa_user_green_developer*.4></color> | Mary details... This is a stdlib sprite |
    | <size:11><back:#DarkGreen>Ivan           </back></size>|    <color:DarkGreen><$osa_user_green_operations*.4></color> | Ivan details... |
    | <size:11><back:#Orange>Bob           </back></size>|    <color:Orange><$osa_user_green_business_manager*.4></color> | Bob details... |
    | <size:11><back:#Purple>Box           </back></size>|    <color:Purple><&box></color> | A Box. This is an openiconic sprite |
endlegend

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml




```



## Conclusion

We went step-by-step through the creation of a network diagram.

Looking at the source code for the diagram, there is very little
redundant information. Most of the text appears in the diagram as text,
the remainder is for the layout direction and the included icons.

Now that we have a template diagram, producing variants of it is even
quicker as we just need to edit the relevant lines of text.
