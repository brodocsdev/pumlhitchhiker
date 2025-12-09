# Create Real Life AWS Diagrams

> In this section we'll put PlantUML to the test by seeing if we can
> recreate some real diagrams from the
> [AWSArchitectureBlog](https://aws.amazon.com/blogs/architecture).
>
> We'll show the original image from the
> [AWSArchitectureBlog](https://aws.amazon.com/blogs/architecture), and
> the PlantUML version for comparison.
>
> **We're aiming for architectural equivalence (not image
> reproduction).**

We take the 3 most recent entries that show architecture diagrams on the
front page of
[AWSArchitectureBlog](https://aws.amazon.com/blogs/architecture) as at
May 2020.

1.  BBVA: Helping Global Remote Working with Amazon AppStream 2.0
    <https://aws.amazon.com/blogs/architecture/bbva-helping-global-remote-working-with-amazon-appstream-2-0/>
2.  Building a Scalable Document Pre-Processing Pipeline
    <https://aws.amazon.com/blogs/architecture/building-a-scalable-document-pre-processing-pipeline/>
3.  Serving Billions of Ads in Just 100 ms Using Amazon Elasticache for
    Redis
    <https://aws.amazon.com/blogs/architecture/serving-billions-of-ads-with-amazon-elasticache-for-redis/>

This sample of 3 diagrams is quite varied in complexity and features.

We'll approach them in order of complexity.

## [AWSArchitectureBlogSample1](#awsarchitectureblogsample1)

### Original

![](/Using%20standard%20library/aws/High-level-digram-1-Smadex-1024x584.png)

### PlantUML Equivalent

[<img src="../res/play.png" width="40" alt="playbutton_aws0" />](http://www.plantuml.com/plantuml/uml/VP3BRnD13CRlyrUOlH0aiX45BX6g6g8AzO24j3pEpewRjU9vC8-cLTN_7IVBAfK8lUnuxD_tVPwzoWLJgKxCA_QzL4lm2VTPUBDO_UhMmRdWBy_EEdPH-9R9jb7rPo1LnrfeWIB_GrpOiBn8RCbJGda9-P92ZJTzyFaPPI3ls4TCw43OKtc81378m-5YNf-RXbI6O4p4VeTRWaOV2Mi9rJRmQAxN5xFEeQNxjz2C1NIKxhYdHZlGl35Fnlp8bFBi-DNcyPoctnDQBXmyoa57QRQor_VzW7vBYgmiJBT9yVNuSsRZeRrlTIES1qg0CK98iAVDn8x9CBTXx-UNC6gMyAw5dvovvBzcC4-y7OeIf_0bNBJG5Km5iFQ73SrfU1ACRrx2-nO-iuL4lolb0WkjSWm-ana9c0lTbcSxV53t8UmrSLpoNykFBToug3vPmzMn5-vtUhBF1KMqeZlo1HwdKBPFvegyhKx-0000_)
Press to play around with this diagram source online.



![](/Using%20standard%20library/aws/1.7.png)



#### Source


```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>

 skinparam linetype polyline
' skinparam linetype ortho

package "AWS Cloud" {
EC2(Smadex, "Smadex Service", " ")
}

Users(Users, "Users", " ")
TraditionalServer(AdExchange, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

Users -down-> Mobile: 1. Visits
Mobile -right-> AdExchange: 2. Start auction
AdExchange -right-> Smadex: 3. Bid request / response
Smadex -left-> Mobile: 4. Show Ad
Users -right-> Smadex: 5. Impression / click / install / event {request id}
@enduml
```


### Select an icon library

These are recent diagrams (April, May 2020) so use the newer AWS icon
set from AWS i.e.

- This one:
  <https://github.com/plantuml/plantuml-stdlib/tree/master/awslib>
- Not this one
  <https://github.com/plantuml/plantuml-stdlib/tree/master/aws>

ref: <https://github.com/awslabs/aws-icons-for-plantuml>

We can see all the icons here:
<https://github.com/awslabs/aws-icons-for-plantuml/blob/master/AWSSymbols.md>

### Find Icons



![](/Using%20standard%20library/aws/1.1.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws1" />](http://www.plantuml.com/plantuml/uml/ROqnoi9044RxFSNyHI1f_bn096AXXOAWOcEpIIRiuEnks9qrhTVmUfx4BKG4xGQ-z-OrKNIGP5dzaUiuzGWpFKMcjbwSzajlhNVpxoqFOnAiDVF_cEqVYFKjyIUXcAB4CP1WL6hmNZ10CMJ8QOjb1G5TZm5xc4WCx5WxEMutSCKGoJieNaTPdTt18An9EcFeWk5nkqTO9SfryMzHDVbVBZy1_)
Press to play around with this diagram source online.

#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

listsprites
@enduml
```



### Gather the icons we need

- For the EC2 icon on right of the diagram; for AWS icons, Orange is AWS
  Compute so we look at the compute icons.
- Use our github trick to find "users"; they are in General.
- The green box isn't an AWS service - it's showing a mobile/laptop
  client.
- We need "Traditional Server" for "Ad Exchange"
- For the box we'll use a
  [Deployment](https://plantuml.com/deployment-diagram) Diagram shape;
  `` `package ``<span class="title-ref"> or </span>`cloud`\`

> `` `autonumber ``\` does not work in these diagrams. So we will
> manually number the arrows.



![](/Using%20standard%20library/aws/1.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws2" />](http://www.plantuml.com/plantuml/uml/VOw_2i8m48VtF4ND544iE8jKYgDJ5UTBSsZWafHBegzlg8lGqE7-SD_tW-jY0axPaTXOFr8ss1pX4ydgzlmO-k1SyASbAs3A2LiWsaybNL5Sq9PMZITwPA0_HLpwWogrQoI1Hf9bIJY-v5RS8t9KSw_G6uEnoGOFD22_aTNYKabTvnVLRrIuwD2RxEWB_)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

EC2(EC2, "label", "tech")
Users(Users, "label", "tech")
TraditionalServer(TraditionalServer, "label", "tech")
Mobile(Mobile, "label", "tech")

@enduml
```



### Add Text To Icons



![](/Using%20standard%20library/aws/1.2.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws3" />](http://www.plantuml.com/plantuml/uml/VOxDIiKm48NtUOgngmZY1TSYztBfKX2gk9uqGnkO_319R1_VMAa85HV9WUzy9-IS2qgfdjMD2oDNI_28IsPdJfVtuHgzZ-7fsBKYrK8dPBvFRVs7ugDn_AynKI11_gMe_lgWsxc3Rl1eQOM1vCEDr3K2tQrwooHPRtSZM-xLgw1rnSM0_3KYqGVIp8k5VXrd3DFFcy_RH_LtDFPI3Riyam2c155W8RExwap1Li-V_)
Press to play around with this diagram source online.

#### Source


```
@startuml
!include <awslib/AWSCommon>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

EC2(EC2, "Smadex Service", " ")
Users(Users, "Users", " ")
TraditionalServer(TraditionalServer, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

@enduml
```



### Simplify The Icons



![](/Using%20standard%20library/aws/1.3.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws4" />](http://www.plantuml.com/plantuml/uml/VOvDImCn443l-ol6FKKG2vv5MagFWX35ysGpjWEJ3oQ9xSythYm8hZqa0s_UWzcMYbfRaE66uoJD4ppYkGYxpUxTxbC8AJwjxYo7BFp1vEzpxrUaNkTMQOCY_oaXEPQhnf4YASelPJZi7qn_Tp3QW9ukO4a_UQAn4nXlXxT2MipyTpBFPVMgwBboYYZV4QdvGxgvyt2uJ2UCHrh2v_bGypCwUsbEk9n80NE6f70cjxZ3bg9lGRu0_)
Press to play around with this diagram source online.

#### Source


```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

EC2(EC2, "Smadex Service", " ")
Users(Users, "Users", " ")
TraditionalServer(TraditionalServer, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

@enduml
```



### Connect The Icons



![](/Using%20standard%20library/aws/1.4.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws5" />](http://www.plantuml.com/plantuml/uml/VP5FIyD04CNl-HHZJn5CYbKlHKfhwS638CG_vqrssWpExiRTJLCGlxlJXj0YrKjcClDxyrx8F4JbOsiukI1RSQiHxbKNcChnuhrOEcESdPtT5MGQfZMXpXlHdu54tRGHnuhvByIualXVOeCMlU8J95aj9sbXbCRT5Opw1WhqMwfm91CONIQl0Nr83q-P7EgmUl5AKoHd5Uz5wDE5NksgMjaD2hBGCBmDYgT3oBGlCdjkIwPGemVLDE0yT5WEREyCcNQTpMRGQwPmdSCR1OeXwIUGUThKKOYZ-HGcEHJxtm6ghVO9a-FoAEW_U0etEJoG1e-VBOO8O-b2usp0f2SWOrp7amotShrsdJWE8N-VlClXqJHo9uYvNAoOgW-fP4DKpDBX5cs4hy6Kz7SoHwjRmpy0_)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

EC2(Smadex, "Smadex Service", " ")
Users(Users, "Users", " ")
TraditionalServer(AdExchange, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

Users -down-> Mobile: 1. Visits
Mobile -right-> AdExchange: 2. Start auction
AdExchange -right-> Smadex: 3. Bid request / response
Smadex -left-> Mobile: 4. Show Ad
Users -right-> Smadex: 5. Impression / click / install / event {request id}
@enduml
```


### Change the Layout: ortho



![](/Using%20standard%20library/aws/1.5.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws6" />](http://www.plantuml.com/plantuml/uml/VL9BZzCm4BxxLmoz42IIYWKk5LfjgNhWW8GK7cSddZQZZX_OJjCAyT-PD4IjKDbBPZpVunihVafPnznRLY_8jTmRX0zwI4pDSlsZtdXhlNkyYzLa0zEEq5H1z7T8eWvzngLc_X_5-eRuMSOU7KRDDnJr4jA1ND1HMs1ocCy18NW-ZmTr3_GnTrwfxUQXgAqsU7eDYwc16kEHMbp811QlrBU4CHMNhqmkTOQ-HcqeatUQHn76OcssfxRJRez2MHkOJxFYy-LsnLHazgLlc5A74NG8u2CCsCpSAHbAumTNFiAaMS6R2hvJefp-ca4PQTzbOLp3L_1GGJt-Hz1zEswehk1LC5ru1Myh-4W68lxiCMLOIfU2TmdLn82ISPTlTdWdxfqV975Uyb_BznLyia5yaeIBOylK7gIIa-V5B1qUqMNuDOUI-QsUq9dnuQa__)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

' skinparam linetype polyline
 skinparam linetype ortho

EC2(Smadex, "Smadex Service", " ")
Users(Users, "Users", " ")
TraditionalServer(AdExchange, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

Users -down-> Mobile: 1. Visits
Mobile -right-> AdExchange: 2. Start auction
AdExchange -right-> Smadex: 3. Bid request / response
Smadex -left-> Mobile: 4. Show Ad
Users -right-> Smadex: 5. Impression / click / install / event {request id}
@enduml


```



### Change the Layout: polyline



![](/Using%20standard%20library/aws/1.6.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws7" />](http://www.plantuml.com/plantuml/uml/VL9BZzCm4BxxLmoz42IIYWKk5LfjgNhWW8GK7cSddZQZZX_OJjCAyT-PD4IjKDbBPZpVunihVafPnznRLY_8jTmRX0zwI4pDSlsZtdXhlNkyYzLa0zEEq5H1z7T8eWvzngLc_X_5-eRuMSOU7KRDDnIL3kI2Zje2ayDy3WZ1ytayg9Tm1_KnTrwfxUQXgAqsU7eDYwc16kEHMbp811QlrBU4CHMNhqmkTOQ-HcqeatUQHn76OcssfxRJRez2MHkOJxFYy-LonLHazgLlc5A74NG8u2CCsCpSAHbAumTNFiAaMS6R2hvJefp-ca4PQTzbOLp3L_1GGJt-Hj1zEswehk1LC5ru1Myh-4W68lxiCMLOIfU2TmdLn82ISPTlTdWdxfqV975Uyb_BznLyia5yaeIBOylK7gIIazV5B1qUqMNuDOUI-QsUq9dUyXy0_)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>

skinparam linetype polyline
' skinparam linetype ortho

EC2(Smadex, "Smadex Service", " ")
Users(Users, "Users", " ")
TraditionalServer(AdExchange, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

Users -down-> Mobile: 1. Visits
Mobile -right-> AdExchange: 2. Start auction
AdExchange -right-> Smadex: 3. Bid request / response
Smadex -left-> Mobile: 4. Show Ad
Users -right-> Smadex: 5. Impression / click / install / event {request id}
@enduml
```



### Add A Box: package



![](/Using%20standard%20library/aws/1.7.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws8" />](http://www.plantuml.com/plantuml/uml/VP3BRnD13CRlyrUOlH0aiX45BX6g6g8AzO24j3pEpewRjU9vC8-cLTN_7IVBAfK8lUnuxD_tVPwzoWLJgKxCA_QzL4lm2VTPUBDO_UhMmRdWBy_EEdPH-9R9jb7rPo1LnrfeWIB_GrpOiBn8RCbJGda9-P92ZJTzyFaPPI3ls4TCw43OKtc81378m-5YNf-RXbI6O4p4VeTRWaOV2Mi9rJRmQAxN5xFEeQNxjz2C1NIKxhYdHZlGl35Fnlp8bFBi-DNcyPoctnDQBXmyoa57QRQor_VzW7vBYgmiJBT9yVNuSsRZeRrlTIES1qg0CK98iAVDn8x9CBTXx-UNC6gMyAw5dvovvBzcC4-y7OeIf_0bNBJG5Km5iFQ73SrfU1ACRrx2-nO-iuL4lolb0WkjSWm-ana9c0lTbcSxV53t8UmrSLpoNykFBToug3vPmzMn5-vtUhBF1KMqeZlo1HwdKBPFvegyhKx-0000_)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>

 skinparam linetype polyline
' skinparam linetype ortho

package "AWS Cloud" {
EC2(Smadex, "Smadex Service", " ")
}

Users(Users, "Users", " ")
TraditionalServer(AdExchange, "Ad Exchange", " ")
Mobile(Mobile, "Publisher app or web", " ")

Users -down-> Mobile: 1. Visits
Mobile -right-> AdExchange: 2. Start auction
AdExchange -right-> Smadex: 3. Bid request / response
Smadex -left-> Mobile: 4. Show Ad
Users -right-> Smadex: 5. Impression / click / install / event {request id}
@enduml
```



## [AWSArchitectureBlogSample2](#awsarchitectureblogsample2)

### Original

### PlantUML Equivalent

[<img src="../res/play.png" width="40" alt="playbutton_aws2_0" />](http://www.plantuml.com/plantuml/uml/hLPTRkCs47xdAQO15bQ0UXSRlmQBTPsV6aZI3RH5NWeKj3IMYL2aG54nqiK2lKQlrvDq98gKR4lgmoQ08l6RRsR8RuOqFvUM6rlbalqaL2Ah5E6IxqifDX-MJ_5AvxbMdmPjiSWBARO2q_S5-G-GoBkeB7xWKevHShqHSfAHeKB3vHJbrkYgM2TQbLEis6h3iybSzrmH8qTbbogzrIze55V9fCkgAgtEqLohh7MTJf3iXC8xv4O9bKrH7z3kjNac5irbfPMbq5Se1KtgTShlYbk-uUNaf9S5LIxXLcYrfi2PQJvx7itVpDVlrfM0pRo4JUcn7SLeNaI2yU9zeJ8s6uaTFyRExeFUyNoJyaFiUdN1PcD5M4bTfK_S9ZldDA1yV1rVvrn8HpWMEoRQFNz6uyopUzTxoo_hMsvnpryTFYbyHxvmx23tiZ8an_zfy5XXXGs9iP9o5Dpm72HDqxuM28MMh_M0pM30getTQQgBrGL8t5eeCQa30vlDV-IF5Jnv9d60zFzphKfRwmtVM5ltQAqoBEj4jAwVuImCWSPd1C3PUU2kTfMgjNDKFuBVJB8Z9yEF_RupDjnDKRo8BS_8cPZBdFz5Vl42MWn-gP9dj3uAAHlHusRMyGa2Xq4ZlASprtoHUtqr8ilGr6vFCJWCMX1kAjLeVEJgpVEgc7-2la2iFsZjOMeiVC4yrNj5jfvWB2mPBhsvNvAsz9HwztQrjpf3kqC3txoATznaU2CaDfeTgjdOe3OUAEfTuvnBEUBQs2PSQTboBAqp3ZWpqYSA4-vfIJXHUjFrDY0ZK5WY-207tH2Mu1s8r617OHpxACGwvnckj7f1Kr9n7EfRYAYD7Jf26-MaoxxNbKurfBpSOTgS0B3HbKgvUGsxzUhkqHMjKIIYuKTofvUFqZTTZ9iMtXHsP4z7c3VjHfruqXcZD2VXDEsqueoTPEZe8oLc8xZRNOEp2SXfaf46O2EuIpAybW0Df9bi4dPQ-LDTGkQwvc55W-QBRYg3zWMZZ1jjhSxVzc2PEDSR0Sg3Ozr1XwTwixVfeLdUS25BlaNtgq80UEHaEuS3nIbiCQrZ3nqgWU2oGqCPF1FMQei6LO9hzQ8JxZUpHw659pQqknr4xjLDmuq3ALmk8cVlWCw5C6Z1se_SmhsczGhZpYb0SAtIGWjbMrzMTr3eXnEnQ_F5j7anOMOdKBSBV1imDhaVGlJ0zn_1CbnhDWp3NEAspZzQMJPg2HbTsIQ8bpxBSHtPCN1C3PNgzkNRtlLOTu-Eki-kLHfiNsDXFpt44JqVEmwDVE-rD-x8Vn3SlE51Mx5jBy6Et4_TzG7rHn_tQjG9MVql83u3OrkjBHfujnKI5SynEWSgG8e6KzWBkuClaYlx-_qT-9_PT-r7TFw7-hf3-5LGhfqWcV_z-vyIRYkH8bWT7DbdYbVbyZy0_)
Press to play around with this diagram source online.



![](/Using%20standard%20library/aws/2.8.png)

In general, I recommend starting a diagram without forcing the arrow
directions to let PlantUML optimise the layout; then tweak the result.

Because we are trying to compare to an existing complex diagram, I will
force the layout to match the original - but only up to a point that
allows clarity and comparison.

Because there are a lot of parts to this diagram, I built it
step-by-step in sections to validate as I went - which makes it easier
to fix a typo, or get feedback as we go. Not all steps are shown here -
only the final ones - but the PlantUML source code files for each step
are in the directory with the source and documentation.



### First Pass



![](/Using%20standard%20library/aws/2.6.png) 



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws2_1" />](http://www.plantuml.com/plantuml/uml/hLPDR-Cs4BtpLqnpaGhKkrZxMYpMTPp0G98sK84S2reQoq8eKg2e66xH_zwHA5AoGwbeDm4SYU-zcQ7cW-2tsd1jcbAm7mgPYYP3-9cVQb7iFwzVaeqgIoM_1hcaA2jH70hCFbLa7n2HTTKO_Co5c9AKQb-8MKME4ZKNSv9xhPfgbofPpwaIepJFPsCzSacA4gLPo-nUlQ6MNAQp9fkcDgf4lPLvRpeV83qM4X-GQrd8V4xwXEQaz2kfQ2yR9GsvlaLHqAREStQttF0zhsStlQweSYatXP8xSfphxlL_M2HFoNz8JB9DjYKlN13wYroBtDigiyXLgUikx5S9whSYnMJrgP8vYwOsyvnOtZbzuEK-uvVOThDaqLITDq8rsGitwT4QpNo35LpNCo7P8tz5RUdeqRRt-hVTFJTuucUBpzPs42-jsbTqtMXAnx_buBd11ZiHOpN5gBZc9GZQfZbN29KIvtR18WYmIfkZeheOLO70Wu4QqzOni6ZnFN-iukah9GSe_t_iP6tQVCDVhAzxl9CvrcqW-gwVuCOlWTOt1C3DZrwxEJQopPsLkXNygjCZ6Mb-RVStO-5kYfDLOdXEngHSb_nFiajMq6FmIvE-ed5UABCn_UpE1Zr1O37e4k_ap3PVR1-_woBFKRTcBmbO37eGxXhPvVZArD6BfbfyXN62s7ZHytvhpB_18bCdITmeOSn_icV75UahJv6F7rPwbxa7hdEyAmHsURhCOCT1IrvaqPac9HTYmhJZPapfKyLKM4i6Z1ab9VOR7kMFS9ACjkiu81B8BGcSauiEy9_W34ZKOLTkhFhAnQxaEMwKV4DTKqKiwjg6f1qFWw3tyhwpgBgPWepNHyoweOUzQcJ6zTaFwEt3CysbEqTYMduXQteu9sDgEKsjFEM6S9H6M7GjPllsiZ4cPJw3yxAhWZFsBi8WdwWmcy3jo0Htuv5Ga63zsGHkWuI_nKE1CBCz4gXy82ykSbjp_qL1UXdSoi2l64NSAsDK-R67oSnHtYMWlZZ9BNHva7UZJJ_QvHqlHCqFIDMrpGeE2KnpVvxO31lCEj-1CyKBR7Je9C4ZOISFg56ck9DlAkLkbXqA7fwSPtiXYErZs8PTUv6_JyIM7u31X33emTQEpFnLfhVowy78Gx2LMQKAQNfRrdQGxuTtoMxfvJozcg7PEsYO0jS6ZCtEW_VkzUx5C-5Qip0C2u67DlvaPTaauoFQih5eKkcZ31LaqV3kQL-NOGe_zZB7XejoFBmEZT5XfnRpq_EKnFJxCcXerNUBkrB7xeNWxWbFoXI7_fPhnUFGiB27pHZorQDOhFtd4UUSVKEPDQNu1m00_)
Press to play around with this diagram source online.

#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/Storage/all.puml>
!include <awslib/ManagementAndGovernance/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/MachineLearning/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/Database/all.puml>
!include <awslib/ApplicationIntegration/all.puml>
!include <awslib/ApplicationIntegration/SNS.puml>
!include <awslib/CustomerEngagement/SESEmail.puml>



'Compute/General
'Storage/SimpleStorageServiceS3.png
'ApplicationIntegration/SQS.png
'Compute/Lambda.png
'Compute/EC2
'ManagementAndGovernance/CloudWatch.png
'CustomerEngagement/SESEmail.png
'MachineLearning/SageMaker.png
''Mobile/APIGateway.png
'NetworkingAndContentDelivery/APIGateway2.png
'Database/Aurora.png
'ApplicationIntegration/SQSQueue.png


skinparam linetype polyline
' skinparam linetype ortho

'top left section 
'-------------------------------------------------------------
package EC2_Instance {
General(IngestionApp, "Ingestion App", " ")
General(ChunkingApp, "Chunking Orchestration App", " ")
}

SimpleStorageServiceS3(S3Staging, "Amazon S3 Staging Bucket", " ")
SQS(SQSIngest, "Amazon SQS Ingest Queue", " ")

Lambda(LambdaTrigger, "AWS Lambda Trigger Function", " ")

LambdaTrigger -up-> IngestionApp
IngestionApp -up-> SQSIngest
SQSIngest -down-> ChunkingApp
S3Staging -down-> EC2_Instance

'top right section 
'-------------------------------------------------------------
SQS(SQSLargeFileQueue, "Amazon SQS Large File Queue", " ")
SQS(SQSSmallFileQueue, "Amazon SQS Small File Queue", " ")
SQS(SQSSingleFileQueue, "Amazon SQS Single File Queue", " ")

EC2(LargeFileChunkingAppEC2, "Large File Chunking App on EC2", " ")
Lambda(LambdaSmallFileChunking, "Small File Chunking Lambda", " ")
Lambda(ImageConversionLambdaFunction, "Image Conversion Lambda Function", " ")

'todo dashed line boundary
package DLQ {
SQSQueue(DLQ1, "DLQ", " ")
SQSQueue(DLQ2, "DLQ", " ")
SQSQueue(DLQ3, "DLQ", " ")
}

ChunkingApp -right-> SQSLargeFileQueue
ChunkingApp -right-> SQSSmallFileQueue
ChunkingApp -right-> SQSSingleFileQueue

SQSLargeFileQueue -right-> LargeFileChunkingAppEC2
LargeFileChunkingAppEC2 -down-> SQSSmallFileQueue
SQSSmallFileQueue -right-> LambdaSmallFileChunking
LambdaSmallFileChunking -down-> SQSSingleFileQueue
SQSSingleFileQueue -right-> ImageConversionLambdaFunction

'todo dashed line
SQSLargeFileQueue -down-> DLQ1
SQSSmallFileQueue -down-> DLQ2
SQSSingleFileQueue -down-> DLQ3


'bottom right section 
'-------------------------------------------------------------

SimpleStorageServiceS3(S3Images, "Amazon S3 Images Bucket", " ")
EC2(EC2DLQFailsafeApp, "DLQ Failsafe App on EC2", " ")
SQS(SQSConvertedImageQueue, "Amazon SQS Converted Image Queue", " ")
Lambda(LambdaInferenceInvocation, "Inference Invocation Lambda Function", " ")
Aurora(Aurora, "Amazon Aurora", " ")
APIGateway(AmazonAPIGateway, "Amazon API Gateway", "")
SageMaker(AmazonSageMaker, "Amazon SageMaker Endpoint", "")

DLQ1 -down-> EC2DLQFailsafeApp
DLQ2 -down-> EC2DLQFailsafeApp
DLQ3 -down-> EC2DLQFailsafeApp

EC2DLQFailsafeApp -right-> S3Images

ImageConversionLambdaFunction -down-> S3Images
S3Images -down-> SQSConvertedImageQueue
SQSConvertedImageQueue -left-> LambdaInferenceInvocation
LambdaInferenceInvocation -down-> Aurora
'LambdaInferenceInvocation -left-> APIGateway
'APIGateway -left-> SageMaker


'bottom left section 
'-------------------------------------------------------------

CloudWatch(CloudWatch, "Amazon Cloudwatch", " ")
SNS(SNS1, "Amazon SNS", "")
SESEmail(SESEmail, "Email Notification", "")

CloudWatch --> DLQ
CloudWatch -down-> SNS1
SNS1 -down-> SESEmail
@enduml
```




### Second Pass: Tweak

1.  For clarity, force the cloudwatch branch to go horizontal and
    connect from left to DLQ.
2.  Use `` `together ``\` to group the SQS and File processing icons.
3.  I did not change the boxes line style or colour.



![](/Using%20standard%20library/aws/2.8.png)



#### Play

[<img src="../res/play.png" width="40" alt="playbutton_aws2_2" />](http://www.plantuml.com/plantuml/uml/hLPTRkCs47xdAQO15bQ0UXSRlmQBTPsV6aZI3RH5NWeKj3IMYL2aG54nqiK2lKQlrvDq98gKR4lgmoQ08l6RRsR8RuOqFvUM6rlbalqaL2Ah5E6IxqifDX-MJ_5AvxbMdmPjiSWBARO2q_S5-G-GoBkeB7xWKevHShqHSfAHeKB3vHJbrkYgM2TQbLEis6h3iybSzrmH8qTbbogzrIze55V9fCkgAgtEqLohh7MTJf3iXC8xv4O9bKrH7z3kjNac5irbfPMbq5Se1KtgTShlYbk-uUNaf9S5LIxXLcYrfi2PQJvx7itVpDVlrfM0pRo4JUcn7SLeNaI2yU9zeJ8s6uaTFyRExeFUyNoJyaFiUdN1PcD5M4bTfK_S9ZldDA1yV1rVvrn8HpWMEoRQFNz6uyopUzTxoo_hMsvnpryTFYbyHxvmx23tiZ8an_zfy5XXXGs9iP9o5Dpm72HDqxuM28MMh_M0pM30getTQQgBrGL8t5eeCQa30vlDV-IF5Jnv9d60zFzphKfRwmtVM5ltQAqoBEj4jAwVuImCWSPd1C3PUU2kTfMgjNDKFuBVJB8Z9yEF_RupDjnDKRo8BS_8cPZBdFz5Vl42MWn-gP9dj3uAAHlHusRMyGa2Xq4ZlASprtoHUtqr8ilGr6vFCJWCMX1kAjLeVEJgpVEgc7-2la2iFsZjOMeiVC4yrNj5jfvWB2mPBhsvNvAsz9HwztQrjpf3kqC3txoATznaU2CaDfeTgjdOe3OUAEfTuvnBEUBQs2PSQTboBAqp3ZWpqYSA4-vfIJXHUjFrDY0ZK5WY-207tH2Mu1s8r617OHpxACGwvnckj7f1Kr9n7EfRYAYD7Jf26-MaoxxNbKurfBpSOTgS0B3HbKgvUGsxzUhkqHMjKIIYuKTofvUFqZTTZ9iMtXHsP4z7c3VjHfruqXcZD2VXDEsqueoTPEZe8oLc8xZRNOEp2SXfaf46O2EuIpAybW0Df9bi4dPQ-LDTGkQwvc55W-QBRYg3zWMZZ1jjhSxVzc2PEDSR0Sg3Ozr1XwTwixVfeLdUS25BlaNtgq80UEHaEuS3nIbiCQrZ3nqgWU2oGqCPF1FMQei6LO9hzQ8JxZUpHw659pQqknr4xjLDmuq3ALmk8cVlWCw5C6Z1se_SmhsczGhZpYb0SAtIGWjbMrzMTr3eXnEnQ_F5j7anOMOdKBSBV1imDhaVGlJ0zn_1CbnhDWp3NEAspZzQMJPg2HbTsIQ8bpxBSHtPCN1C3PNgzkNRtlLOTu-Eki-kLHfiNsDXFpt44JqVEmwDVE-rD-x8Vn3SlE51Mx5jBy6Et4_TzG7rHn_tQjG9MVql83u3OrkjBHfujnKI5SynEWSgG8e6KzWBkuClaYlx-_qT-9_PT-r7TFw7-hf3-5LGhfqWcV_z-vyIRYkH8bWT7DbdYbVbyZy0_)
Press to play around with this diagram source online.

#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/Storage/all.puml>
!include <awslib/ManagementAndGovernance/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/MachineLearning/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/Database/all.puml>
!include <awslib/ApplicationIntegration/all.puml>





'Compute/General
'Storage/SimpleStorageServiceS3.png
'ApplicationIntegration/SQS.png
'Compute/Lambda.png
'Compute/EC2
'ManagementAndGovernance/CloudWatch.png
'CustomerEngagement/SESEmail.png
'MachineLearning/SageMaker.png
''Mobile/APIGateway.png
'NetworkingAndContentDelivery/APIGateway2.png
'Database/Aurora.png
'ApplicationIntegration/SQSQueue.png


skinparam linetype polyline
' skinparam linetype ortho

'top left section 
'-------------------------------------------------------------
package EC2_Instance {
General(IngestionApp, "Ingestion App", " ")
General(ChunkingApp, "Chunking Orchestration App", " ")
}

SimpleStorageServiceS3(S3Staging, "Amazon S3 Staging Bucket", " ")
SQS(SQSIngest, "Amazon SQS Ingest Queue", " ")

Lambda(LambdaTrigger, "AWS Lambda Trigger Function", " ")

LambdaTrigger -up-> IngestionApp
IngestionApp -up-> SQSIngest
SQSIngest -down-> ChunkingApp
S3Staging <-down-> EC2_Instance

'top right section 
'-------------------------------------------------------------
together {
SQS(SQSLargeFileQueue, "Amazon SQS Large File Queue", " ")
SQS(SQSSmallFileQueue, "Amazon SQS Small File Queue", " ")
SQS(SQSSingleFileQueue, "Amazon SQS Single File Queue", " ")

EC2(LargeFileChunkingAppEC2, "Large File Chunking App on EC2", " ")
Lambda(LambdaSmallFileChunking, "Small File Chunking Lambda", " ")
Lambda(ImageConversionLambdaFunction, "Image Conversion Lambda Function", " ")
}
'todo dashed line boundary
package DLQ {
SQSQueue(DLQ1, "DLQ", " ")
SQSQueue(DLQ2, "DLQ", " ")
SQSQueue(DLQ3, "DLQ", " ")
}

ChunkingApp -right-> SQSLargeFileQueue
ChunkingApp -right-> SQSSmallFileQueue
ChunkingApp -right-> SQSSingleFileQueue

SQSLargeFileQueue -right-> LargeFileChunkingAppEC2
LargeFileChunkingAppEC2 -down-> SQSSmallFileQueue
SQSSmallFileQueue -right-> LambdaSmallFileChunking
LambdaSmallFileChunking -down-> SQSSingleFileQueue
SQSSingleFileQueue -right-> ImageConversionLambdaFunction

'todo dashed line
SQSLargeFileQueue -down-> DLQ1
SQSSmallFileQueue -down-> DLQ2
SQSSingleFileQueue -down-> DLQ3


'bottom right section 
'-------------------------------------------------------------

SimpleStorageServiceS3(S3Images, "Amazon S3 Images Bucket", " ")
EC2(EC2DLQFailsafeApp, "DLQ Failsafe App on EC2", " ")
SQS(SQSConvertedImageQueue, "Amazon SQS Converted Image Queue", " ")
Lambda(LambdaInferenceInvocation, "Inference Invocation Lambda Function", " ")
Aurora(Aurora, "Amazon Aurora", " ")
APIGateway(AmazonAPIGateway, "Amazon API Gateway", "")
SageMaker(AmazonSageMaker, "Amazon SageMaker Endpoint", "")

DLQ1 -down-> EC2DLQFailsafeApp
DLQ2 -down-> EC2DLQFailsafeApp
DLQ3 -down-> EC2DLQFailsafeApp

EC2DLQFailsafeApp -right-> S3Images

ImageConversionLambdaFunction -down-> S3Images
S3Images -down-> SQSConvertedImageQueue
SQSConvertedImageQueue -left-> LambdaInferenceInvocation
LambdaInferenceInvocation -down-> Aurora
LambdaInferenceInvocation <-left-> AmazonAPIGateway
AmazonAPIGateway <-left-> AmazonSageMaker


'bottom left section 
'-------------------------------------------------------------

CloudWatch(CloudWatch, "Amazon Cloudwatch", " ")
SNS(SNS1, "Amazon SNS", "")
SESEmail(SESEmail, "Email Notification", "")

CloudWatch -right-> DLQ
CloudWatch -left-> SNS1
SNS1 -left-> SESEmail

footer %filename() rendered with PlantUML version %version()\nThe Hitchhiker’s Guide to PlantUML
@enduml
```




## [AWSArchitectureBlogSample3](#awsarchitectureblogsample3)

### PlantUML Equivalent

[<img src="../res/play.png" width="40" alt="playbutton_aws30" />](http://www.plantuml.com/plantuml/uml/VP3BRnD13CRlyrUOlH0aiX45BX6g6g8AzO24j3pEpewRjU9vC8-cLTN_7IVBAfK8lUnuxD_tVPwzoWLJgKxCA_QzL4lm2VTPUBDO_UhMmRdWBy_EEdPH-9R9jb7rPo1LnrfeWIB_GrpOiBn8RCbJGda9-P92ZJTzyFaPPI3ls4TCw43OKtc81378m-5YNf-RXbI6O4p4VeTRWaOV2Mi9rJRmQAxN5xFEeQNxjz2C1NIKxhYdHZlGl35Fnlp8bFBi-DNcyPoctnDQBXmyoa57QRQor_VzW7vBYgmiJBT9yVNuSsRZeRrlTIES1qg0CK98iAVDn8x9CBTXx-UNC6gMyAw5dvovvBzcC4-y7OeIf_0bNBJG5Km5iFQ73SrfU1ACRrx2-nO-iuL4lolb0WkjSWm-ana9c0lTbcSxV53t8UmrSLpoNykFBToug3vPmzMn5-vtUhBF1KMqeZlo1HwdKBPFvegyhKx-0000_)
Press to play around with this diagram source online.



![](/Using%20standard%20library/aws/3.8.png)



#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/EndUserComputing/all.puml>
!include <awslib/ApplicationIntegration/all.puml>

'skinparam linetype polyline


!unquoted procedure $PublicSubnet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> e6ffef
        borderColor<<$alias>> e6ffef
        shadowing<<$alias>> true
    }
    rectangle $alias <<$alias>> as "
        <color:3F8624><$VPCSubnetPublic*.4> Public Subnet</color>\n
        <color:$colour><$MySprite></color>\n$label" 

!endprocedure

!unquoted procedure $PrivateSubnet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> e6fbff
        borderColor<<$alias>> e6fbff
        shadowing<<$alias>> true
    }
    
    rectangle $alias <<$alias>> as "
        <color:3B48CC><$VPCSubnetPrivate*.4> Private Subnet</color>\n
        <color:$colour><$MySprite></color>\n$label" 

!endprocedure


!unquoted procedure $VPCNet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> white
        borderColor<<$alias>> e6fbff
        shadowing<<$alias>> true
    }
    
    rectangle $alias <<$alias>> as "
        <color:3F8624><$VPC*.4></color> <color:grey>$label</color>\n
        <color:$colour><$MySprite></color>\n$description" 

!endprocedure

'note the "=" denotes heading 1
skinparam rectangle {
        backgroundColor<<BBVA>> white
        borderColor<<BBVA>> white
        shadowing<<$alias>> false
    }
rectangle  BBVA <<BBVA>> as "
        =<color:blue>BBVA</color>\n
        \nAuthentication Service" 



AutoScalingGroup(AutoScalingGroup1, "Auto Scaling Group", "")
ELBNetworkLoadBalancer(ELBNetworkLoadBalancer, "Network Load Balancer", " ")
VPCInternetGateway(VPCInternetGateway, "Internet Gateway", " ")
InternetAlt1(InternetAlt1, "Internet", " ")
'VPCElasticNetworkInterface(VPCElasticNetworkInterface, " ", " ")

VPCInternetGateway -u-> InternetAlt1
VPCVPNConnection(VPCVPNConnection, "VPN\nConnection", " ")
DirectConnect(DirectConnect, "Direct\nConnect", " ")
TransitGateway(S3TransitGatewayStaging, "TransitGateway", " ")

VPCCustomerGateway(VPCCustomerGateway, " ", " ")
'Appstream2_0(Appstream2_0, " ", " ")
Cloudalt(Cloudalt, " ", " ")
User(User, "BBVA Employee", " ")


'package "BBVA VPC 2"
'{

    'package "Availability Zone 1"
    '{

        $PublicSubnet($EC2Instance, EC2Instance1, $label="Proxy Instance",  $colour="D86613")

        $PrivateSubnet($ELBNetworkLoadBalancer, ELBNetworkLoadBalancer1, $colour="D86613")

        EC2Instance1 --[hidden]> ELBNetworkLoadBalancer1

    '}


    'package "Availability Zone 2"
    '{

        $PublicSubnet($EC2Instance, EC2Instance2, $label="Proxy Instance",  $colour="D86613")

        $PrivateSubnet($ELBNetworkLoadBalancer, ELBNetworkLoadBalancer2, $colour="D86613")

        EC2Instance2 --[hidden]> ELBNetworkLoadBalancer2

    '}
'}


$VPCNet($VPCElasticNetworkInterface, VPCElasticNetworkInterface2, $label="BBVA VPC 1", $colour="purple")
$VPCNet($Appstream2_0, Appstream2_02, $label="Appstream 2.0 VPC", $description="Appstream 2.0", $colour="purple")
'$MyOnPrem($VPCCustomerGateway, $label="Customer Gateway")

EC2Instance1 -r-> AutoScalingGroup1
AutoScalingGroup1 -r-> EC2Instance2

ELBNetworkLoadBalancer1 -r-> ELBNetworkLoadBalancer
ELBNetworkLoadBalancer -r->ELBNetworkLoadBalancer2

S3TransitGatewayStaging -u-> DirectConnect
S3TransitGatewayStaging -u-> VPCVPNConnection
S3TransitGatewayStaging -> EC2Instance1
DirectConnect -u-> VPCCustomerGateway
VPCVPNConnection -u-> VPCCustomerGateway

Appstream2_02 -d-> VPCElasticNetworkInterface2 
VPCElasticNetworkInterface2 -> S3TransitGatewayStaging


User -d-> BBVA 
BBVA -d-> Appstream2_02


@enduml

  
    
```


### Gather the icons we need

> When using `` `listsprites ``\` limit the number of library categories
> you include to make it easier to search category by category.
> Simplified off (by commenting out the simplified header) so we can see
> the icon name.



![](/Using%20standard%20library/aws/3.1.png)



#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
'!include <awslib/Compute/all.puml>
'!include <awslib/mobile/all.puml>
'!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/EndUserComputing/all.puml>
!include <awslib/ApplicationIntegration/all.puml>

listsprites

'Appstream2_0
'AutoScalingGroup
'EC2Instance
'InternetAlt1
'DirectConnect
'VPCVPNConnection
'VPCSubnetPublic
'VPCSubnetPrivate
'VPCInternetGateway
'VPCCustomerGateway
'TransitGateway
'VPCElasticNetworkInterface
'ELBNetworkLoadBalancer

'Cloudalt

@enduml
```


### Add Text and Simplify The Icons



![](/Using%20standard%20library/aws/3.3.png)



#### Source



```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/EndUserComputing/all.puml>
!include <awslib/ApplicationIntegration/all.puml>


Appstream2_0(Appstream2_0, " ", " ")
AutoScalingGroup(AutoScalingGroup, " ", " ")
EC2Instance(EC2Instance, " ", " ")
InternetAlt1(InternetAlt1, " ", " ")
DirectConnect(DirectConnect, " ", " ")
VPCVPNConnection(VPCVPNConnection, " ", " ")
VPCSubnetPublic(VPCSubnetPublic, " ", " ")
VPCSubnetPrivate(VPCSubnetPrivate, " ", " ")
VPCInternetGateway(VPCInternetGateway, " ", " ")
VPCCustomerGateway(VPCCustomerGateway, " ", " ")
TransitGateway(S3TransitGatewayStaging, " ", " ")
VPCElasticNetworkInterface(VPCElasticNetworkInterface, " ", " ")
ELBNetworkLoadBalancer(ELBNetworkLoadBalancer, " ", " ")

Cloudalt(Cloudalt, " ", " ")

@enduml
```




### Draw Boxes



![](/Using%20standard%20library/aws/3.4.png)



#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/EndUserComputing/all.puml>
!include <awslib/ApplicationIntegration/all.puml>


skinparam rectangle {
    backgroundColor<<box1>> e6fbff
    borderColor<<$box1>> e6fbff
    shadowing<<$box1>> true
    
    backgroundColor<<box2>> e6ffef
    borderColor<<$box2>> e6ffef
    shadowing<<$box2>> true
}

package "AZ"
{

rectangle box2 <<box2>> as "<color:3F8624><$VPCSubnetPublic*.4> Public Subnet</color>\n
    <color:D86613><$EC2Instance></color>\nProxy Instance" 

rectangle box1 <<box1>> as "<color:3B48CC><$VPCSubnetPrivate*.4> Private Subnet</color>\n
    <color:D86613><$ELBNetworkLoadBalancer></color>\n" 
}
@enduml
```


### Draw Boxes with Procedures

In this case, we create everything we need ourselves like VPC compound
components. It is informative to see how to do it.

In the future, this functionality could be part of stdlib so we don't
have to.



![](/Using%20standard%20library/aws/3.8.png)



#### Source

```
@startuml
!include <awslib/AWSCommon>
!include <awslib/AWSSimplified.puml>
!include <awslib/Compute/all.puml>
!include <awslib/mobile/all.puml>
!include <awslib/general/all.puml>
!include <awslib/GroupIcons/all.puml>
!include <awslib/CustomerEngagement/all.puml>
!include <awslib/NetworkingAndContentDelivery/all.puml>
!include <awslib/EndUserComputing/all.puml>
!include <awslib/ApplicationIntegration/all.puml>

'skinparam linetype polyline


!unquoted procedure $PublicSubnet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> e6ffef
        borderColor<<$alias>> e6ffef
        shadowing<<$alias>> true
    }
    rectangle $alias <<$alias>> as "
        <color:3F8624><$VPCSubnetPublic*.4> Public Subnet</color>\n
        <color:$colour><$MySprite></color>\n$label" 

!endprocedure

!unquoted procedure $PrivateSubnet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> e6fbff
        borderColor<<$alias>> e6fbff
        shadowing<<$alias>> true
    }
    
    rectangle $alias <<$alias>> as "
        <color:3B48CC><$VPCSubnetPrivate*.4> Private Subnet</color>\n
        <color:$colour><$MySprite></color>\n$label" 

!endprocedure


!unquoted procedure $VPCNet($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="", $textsize="18")

    skinparam rectangle {
        backgroundColor<<$alias>> white
        borderColor<<$alias>> e6fbff
        shadowing<<$alias>> true
    }
    
    rectangle $alias <<$alias>> as "
        <color:3F8624><$VPC*.4></color> <color:grey>$label</color>\n
        <color:$colour><$MySprite></color>\n$description" 

!endprocedure

'note the "=" denotes heading 1
skinparam rectangle {
        backgroundColor<<BBVA>> white
        borderColor<<BBVA>> white
        shadowing<<$alias>> false
    }
rectangle  BBVA <<BBVA>> as "
        =<color:blue>BBVA</color>\n
        \nAuthentication Service" 



AutoScalingGroup(AutoScalingGroup1, "Auto Scaling Group", "")
ELBNetworkLoadBalancer(ELBNetworkLoadBalancer, "Network Load Balancer", " ")
VPCInternetGateway(VPCInternetGateway, "Internet Gateway", " ")
InternetAlt1(InternetAlt1, "Internet", " ")
'VPCElasticNetworkInterface(VPCElasticNetworkInterface, " ", " ")

VPCInternetGateway -u-> InternetAlt1
VPCVPNConnection(VPCVPNConnection, "VPN\nConnection", " ")
DirectConnect(DirectConnect, "Direct\nConnect", " ")
TransitGateway(S3TransitGatewayStaging, "TransitGateway", " ")

VPCCustomerGateway(VPCCustomerGateway, " ", " ")
'Appstream2_0(Appstream2_0, " ", " ")
Cloudalt(Cloudalt, " ", " ")
User(User, "BBVA Employee", " ")


'package "BBVA VPC 2"
'{

    'package "Availability Zone 1"
    '{

        $PublicSubnet($EC2Instance, EC2Instance1, $label="Proxy Instance",  $colour="D86613")

        $PrivateSubnet($ELBNetworkLoadBalancer, ELBNetworkLoadBalancer1, $colour="D86613")

        EC2Instance1 --[hidden]> ELBNetworkLoadBalancer1

    '}


    'package "Availability Zone 2"
    '{

        $PublicSubnet($EC2Instance, EC2Instance2, $label="Proxy Instance",  $colour="D86613")

        $PrivateSubnet($ELBNetworkLoadBalancer, ELBNetworkLoadBalancer2, $colour="D86613")

        EC2Instance2 --[hidden]> ELBNetworkLoadBalancer2

    '}
'}


$VPCNet($VPCElasticNetworkInterface, VPCElasticNetworkInterface2, $label="BBVA VPC 1", $colour="purple")
$VPCNet($Appstream2_0, Appstream2_02, $label="Appstream 2.0 VPC", $description="Appstream 2.0", $colour="purple")
'$MyOnPrem($VPCCustomerGateway, $label="Customer Gateway")

EC2Instance1 -r-> AutoScalingGroup1
AutoScalingGroup1 -r-> EC2Instance2

ELBNetworkLoadBalancer1 -r-> ELBNetworkLoadBalancer
ELBNetworkLoadBalancer -r->ELBNetworkLoadBalancer2

S3TransitGatewayStaging -u-> DirectConnect
S3TransitGatewayStaging -u-> VPCVPNConnection
S3TransitGatewayStaging -> EC2Instance1
DirectConnect -u-> VPCCustomerGateway
VPCVPNConnection -u-> VPCCustomerGateway

Appstream2_02 -d-> VPCElasticNetworkInterface2 
VPCElasticNetworkInterface2 -> S3TransitGatewayStaging


User -d-> BBVA 
BBVA -d-> Appstream2_02


@enduml

  
    
```
