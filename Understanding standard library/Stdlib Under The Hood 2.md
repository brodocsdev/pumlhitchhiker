# PlantUML Stdlib Under The Hood 2

## Step-by-step Towards A Standard Macro


![](/Stdlib/ProcedureBuildup.png)


```
@startuml
'create equivalent of icons shown here https://github.com/awslabs/aws-icons-for-plantuml


sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}


rectangle "<color:red><$Batch></color>\n0"  as rectangle


'Render a sprite
!procedure $ffoo1()
    rectangle "<$Batch>\n1"
!endprocedure

$ffoo1()


'Render a sprite - with color red
!procedure $ffoo2()
    rectangle "<color:red><$Batch></color>\n2" as 2
!endprocedure

$ffoo2()


'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/General/Disk.puml
'rectangle "==e_label\n<color:e_color><$e_sprite></color>\n//<size:TECHN_FONT_SIZE>[e_techn]</size>//" <<e_stereo>> as e_alias
'!define DiskParticipant(p_alias, p_label, p_techn, p_descr) AWSParticipant(p_alias, p_label, p_techn, p_descr, #232F3E, Disk, Disk)
'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/source/AWSCommon.puml
'common.puml: rectangle "==e_label\n<color:e_color><$e_sprite></color>\n//<size:TECHN_FONT_SIZE>[e_techn]</size>//\n\n e_descr" <<e_stereo>> as e_alias


'Render a sprite - with color red - and add some text
!procedure $ffoo3()
    rectangle "==label\n<color:red><$Batch></color>\n[technology]\n\n Description 3" as 3
!endprocedure

$ffoo3()


'Render a sprite - with color red - and add some text - with some formatting
!procedure $ffoo4()
    rectangle "<<something>>\n==label\n<color:red><$Batch></color>\n//<size:12>[technology]</size>//\n\n  Description 4" as 4
!endprocedure

$ffoo4()



'!procedure $ffoo5($alias, $description="", $label="", $technology="", $scale=1, $colour=red)
'OBSERVATION 1: the next line does not work - sprite is white - not red;  there is where the unquoted keyword comes in
'rectangle "<<$alias>>\n==$label\n<color:$colour><$Batch*$scale></color>\n//<size:12>[$technology]</size>//\n\n  $description 5" as 5
'the next line works i.e. sprite is red
'rectangle "<<//$alias//>>\n==$label\n"<color:red><$Batch*$scale></color>"\n//<size:12>[$technology]</size>//\n\n  $description 5" as $alias
'!endprocedure

'$ffoo5("myalias", "mydescription", "mylabel", "mytechnology", 2, blue)




'unquoted means that you don't have to use quotes when calling the procedure
!unquoted procedure $ffoo51($alias, $description="", $label="", $technology="", $scale=1, $colour=red)
    rectangle "<<$alias>>\n==$label\n<color:$colour><$Batch*$scale></color>\n//<size:12>[$technology]</size>//\n\n  $description 51" as 5
!endprocedure

$ffoo51(myalias, mydescription, mylabel, mytechnology, 2, blue)


!procedure $ffoo6($alias, $description="", $label="", $technology="", $scale=1, $colour=red)
    rectangle "<<//$alias//>>\n==$label\n<color:red><$Batch*$scale></color>\n//<size:12>[$technology]</size>//\n\n  $description 6 " as $alias
!endprocedure

$ffoo6("myaliasbatch2", "mydescription", "mylabel", "mytechnology", 2, blue)



'OBSERVATION 2: can't do something like this 
'    $ffoo6($scale=2)

@enduml
```


## Close But...

We can use the
[DefaultArgumentValue](https://plantuml.com/preprocessing#ae1b47605326b65f)
to avoid having to specify a parameter value when we call our procedure.
BUT this only works if the default parameters are at the end i.e. it is
all based on the order of the procedure parameters.

*In other words, the user has to know/care about the order of
parameters.*

See `Standard Library - What We Have And What We Want`.

To specify color blue I need to do

`` `$ffoo6("myaliasbatch2", "mydescription", "mylabel", "mytechnology", 2, blue) ``\`

What I want to do `` `$ffoo6($color=blue) ``<span class="title-ref"> or
</span>`$ffoo6($scale=2)`\`

## Procedure Keyword Arguments

To enable the StdLib standardisation, I suggested the *keyword
arguments* and Arnaud produced a release to play with next day - and
this became part of an official release:


![](/Stdlib/pre-processing.png)


```
@startuml

'all sprites in a category would be included in an all.puml file for that category
'==================================================================================================

'create equivalent of icons shown here https://github.com/awslabs/aws-icons-for-plantuml
sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}

'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/ARVR/ARVR.puml
sprite $Arvr [64x64/16z] {
xTG3WiH054NHzutP_th7RHkfsmnEdE1HZMZsIn0_DGDuuVsZJwnMVJ-57txuuKrsP4Tv1mjl3Nw43qZlo147VO9xPueyu8j1l3jm7V0GtPFWe8_UKzpL3rzc
TO4l0gZEzufCsDd-rnhoN2zKtKLoWk-bkHq--vabr0TypEy_WiwEmc9K7FATAd_fVDwOZygdU_uEF_pmLgUMA_wChkV1SavCc4LdXNVe2m
}

'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/ARVR/Sumerian.puml
sprite $Sumerian [64x64/16z] {
xPO5qkim38HN3FU_xuE29mMx-Hbtg4to6GIZxVVJhtvLLI-XbK2QJo6sVv90JA3SImUJRVuAjBeDl8zE0G2EyVy42d87NGOmGG0vVHuu7iRWZt4daBUWWW6j
8w_zNufuHES9KgxpKjr5o6CKQyh5uGi59BTfEuR1GHvEi6cu0N2sWE8sb99j03370L41CkryG9FQh6rTffOJlEWGLz-cbv5N4Pqh83Vf5THL67BA-qXltEu_
2XWrtrzlzZUfwuBCdjy_3ilGeY0Pgmj0NO5ehtb1vh9c0OhsaV_Qfa_hKUzKUDIs_eJgy7myMFEPLzinwd3nSQ0rpwYR_kiWmAgVmezmYuKSJ_94VZJDABad
y4EnAVcdyy4Xo6H_7g-02Se1oIVprMqKX_YdW9_AEtjtdVlNiykVmAS0Tjd_1exTl8wS3Ju5q5sydGux-94Dty4xGtfeyAEewG4FQCvv0vQy0b8zvuiN_EYw
AHy0nu8Ue-gMJrFBOgjTKr_pYfyChlaOjDhmay6vj0xaWvyFxdKOyiYlZSFQGGZIVMbSrhaa46WOf-dmcOS1a3mPjp9mFqqf77FZ-7JZ-Y76UQvV_Uel
}


' sprite decorator is defined once only - not once per sprite as per current puml files in stdlib
'==================================================================================================

' We define 1 or more sprite decorators in stdlib
'---------------------------------------------------
!unquoted procedure $SpriteDecorator($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="red")

rectangle $alias as "
<<$alias>>
$label
<color:$colour><$MySprite*$scale></color>
//<size:12>[$technology]</size>//

  $description"
!endprocedure

'stdlib macros pass the sprite to the decorator - and the other parameters
'all this would happen in an all.puml file per sprite category
'==================================================================================================
!unquoted procedure $BATCH($alias, $description="", $label="", $technology="", $scale=1, $colour="red")
$SpriteDecorator($Batch, $alias, $description, $label, $technology, $scale, $colour)
!endprocedure

!unquoted procedure $ARVR($alias, $description="", $label="", $technology="", $scale=1, $colour="red")
$SpriteDecorator($Arvr, $alias, $description, $label, $technology, $scale, $colour)
!endprocedure

!unquoted procedure $SUMERIAN($alias, $description="", $label="", $technology="", $scale=1, $colour="red")
$SpriteDecorator($Sumerian, $alias, $description, $label, $technology, $scale, $colour)
!endprocedure




'user code
'================
$BATCH(BATCH, $scale=2)

$ARVR(ARVR, "description\non several lines", $scale=.9, $colour="blue")

$SUMERIAN(SUMERIAN, "other description", $label="sdsd", $scale=1.4)


'TODO: play with this to see if "Dynamic invocation" could be useful here? 
' i.e. given 
'   a sprite
'   a decorator function/procedure with params ($alias, $description, $label, $technology, $scale, $colour)
' %call_user_func("decorator", "$sprite")
' this would reduce the duplication even further in examples below 
@enduml

```


## Extensibility

So now we have a way for the user to specify any or all of the sprite
parameters.

But what happens if we want to add new parameters in the future?

### Option 1: Reserve Parameters

One option is to reserve parameters in the procedure definition:

``` 
!unquoted procedure $SpriteDecorator($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="red", $res1="", $res2="", $res3="", $res4="")
```

and used a function/procedure to map the new parameter feature to a
reserved word.

We're not smart enough to predict the future, and we don't want to
impose limits, so we won't be doing this.

### Option 2: Dynamic Invocation

See `stdlibreqs-label` for requirements for stdlib.

Let's define 3 SpriteDecorator Procedures that change the sprite
parameters per `stdlibreqs-label`, where each procedure adds more
parameters than the previous one.

```
    !unquoted procedure $SpriteDecorator($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="red")
    !unquoted procedure $SpriteDecorator2($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="green", $shape="node")
    !unquoted procedure $SpriteDecorator3($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="cloud", $textsize="18")

```

When we define the procedure for the user to call e.g. \$BATCH_DYN, we
specify which SpriteDecorator to be used via \$dynN dynamic invocation.

If at some point later, a new SpriteDecorator becomes available with
same parameters but different processing, or with new parameters, then
we can change this dynN to the new procedure.

#### User code

Parameters

1.  can use ordered list of parameters up to the one they want to
    specify.
2.  can use named arguments to specify only the parameter(s) they care
    about.

Existing code does not need to know or care that the SpriteDecorator has
changed.

New code can use the new decorator functionality if desired.

Play with
[StdlibProposalCode](http://www.plantuml.com/plantuml/uml/j911YiCm34NtFiLV36ILP3ymCCnD54U93OhjiUI6thvk2hr1XK0WwIt--rMZQkqGDv08jDHeh8W914_6UwvtdBd9YeNxsajRURtklKMcqbbiKHXRhh10zkRSyFFnScxmbSaO_D_YZOIJ8M-8FYU5Xdmc1AwCO5RqUvxtQA4jay_7JASABVgSu_K_zWXZ4KgNa9SBVFsH-O07g_Ioyo1JW75ytwlm1l0TpcL9Mw052hJ0q6BC15xEC2q71XYCzwunCT5lP-BcMJpBVtv_aOHD4dvOQV_hd_vssEo7d3Orvi4vs_KTpXfaQstqMhCFvFgDnIIwMDgJD7eidlhZk_MNEs1PMDnt_qAv-ygQTPQU3NN6NOTJZzpQxmqtr0WdUeA23HKHlJvK16aV2IHugerhaIER7bu9MD8Nxrgw8Px1xUxOT7kfYFUMIAo6g-_g9m-vIoi0NghUDUZDB3YNmqLIGIde3r2vAoqtlsuDD_ciBAkIPVxYxTKuzVEYdV67OxSjQ4qFECASKTR0H0mu8pf8jDHjD0tfnZkBYdGupsYiaSwUOsTC61O4lLCjSEGiuvV2ivjzJzJl-eLfpcpimoLtUGdfQmf2rH-CmG2FlZ1BZzE-4Y2YmXGs_EvLbJaj5mNvfHyuLr9L6nq8b2t3SrokemahbplRt-iB2x7kN9NRoNPoVbFv0SYvCzqfYhANvg-Xq3nnbcajeuV4qvjchkf1rGmOxiUn6_1aiPzgVdTjj_Jo4ZsBDW5DwDo2C0lsSjFfRcy7vjPMw9tXzuWeC0v__oUr_ndHJzfzqn-SJ7C-_cJrDF-eJ_Zyr_ov_qzawhYCVpGM67nKNu4eEDUTp1wQA_bvROi9VxHCOw_nFPvk7u0kneKGECNc-hb3an7bUIF46YTF21OMDntlh08_nDsN5MJeAfj7SagE3Tln3POXC6PFZ_8Z2gszj_bn_pq4hj21CjPsKfodIyQCd-hhSBirM_OtQfcqlGuCioJf20BQQnH5zQhXNyMITJLGCrJ0o-h6jCn2H3GTzTWkmxkArdFLGjPFblElO6Sl1-OS_hz6zGdEnphv_7VOVxz_ZEkvuj3Mc3zU7LuFqKOqJi7tZRccSodCNycunHk4PZKljdrZNgd5FSolDC550QRA-pSScaz8rEQKNxhZhW63qoYa0fSTPSTmiM601Lu9aUjd5Cz2bfp2A8gavd1SqUwGWbmrNx7AhRUQKVnAP-j1Av4OjQYSWa8ZJzQuBbej_HBWS5Ea7QTKKHh0ypAm1VRSZjHGz4SbZK5Hk6QdHOQzCx_f8Zg2DrH77XPYSBKb-QGomwkRDO8Et2iQvt7lzZWiLd8wPmr5VDqP-Hju9Mw0uufvDQViKYc_mAsc1A97aQ3A2dShlDmcb9ibbJ6zwvfdx_LdpVYF_m1ZlxwVgAqZh9OGvpj-4yitaIB0sBoefoGxK47xgF0terHuVQKhaai6S7xEVc-m7--3zKBlB5AGgitDdC7EgMaBiUg3eCaGcsz1TrnztYJY84uqCyZ6AC9bfi9cp4LELIrV3K5_d9S5B0yAqkE-aDf1sdizg5SAFkGOvanvDqVzv9PDO8seVnVqN7M9srmgd51fQS2MH0lLjynoQVtkObz_64PyW_VK7wia4QJ8BPWC_xe-c_3OQte5wyDGoB8UCx8PCszP2X_BFwgl_jwsRI3wlpx5HSZWU7NiMDg08N2CPKs15LXI83ys3CDWqEBP9YAH7ab5qpxzZfGYEv7Lf5jTe4KAYzJnlVlnU29_dTrXwXGTlF3XepxxuVhyziFrpIk-Rptu3O7ZGaY4CIWDcT88jRev9aepgxJ_OXlBKp6d5HULkShrjeN_DXS8zr8LuFuV0vCS4YO1cH5f-KWZiG0bqMCkSfiJNq5x4vY1Z4bRUeCrqon3YmHCZCmuv8BU3XeUhcJF0ZwWh2ZPNEKMIhHa_mlQdW73IhZnaLmykWd2r6vmYbGIwtZmt2Pg6qKjexXj50Uzuq__5npaygzSMO9PQvKWT_auVCPsT7XPLbC3E6IfO8P-EPf4YxKLIfw58KsaR8vfzMWnMKcLgcLPZKt2KZmRqrD2ixa-2pNoi1y46XFBv3B56XVeBmmcaseqdGOLQZ1nw_HflNmwQHpwjiAUJaRUOXgCHXCZ_i7JSJJzOykFFoSZDpqTZO80dZWV1WSeUHCyoPjn3ipBmApO6ZTYs5-6epsaUAaHfN_beZWBfUBeSkx7NqV2uGtDM_pR4jGNgKEyXphCqnotof3GB7VZEYwQ6l-mnxeqFAyi3xJh0nQDXPlRyzltRu5OKb2BxTxh-wTX6VgBoN-hJgldXDNLX38L6ikiI6R4E0xxBSjejsdKbdwhshjNnX-lLdGIzfkaNFn-TNwvlwpqxCerUeK6fB9GA7qFNBYkcPR0J4k_S0n6LPyd4BAoT7PhrB1GQQeA8PUG2ed1mI4l9Pn1M6E4Ro1iSCBW6o4Vr3tE6XqSEVi1R6MCnYohw-B76n6veHUiUzYeZX9NyKPTn54NSzH57JMWSHTet0KQTu76OV_5WywxgmlufCEEGuJR5S8SMMxBwkOkwgFBGcbWi1GFABrU1b2WFxqaAoQNsBpBMA8LvEk2QMxWQ9vRhmok2kcd-iI1m-LmU-rFvxTlVvwHLA7AWk-0lEg02wqog4fhbN-8cgSOq2R3uH30oT0xO4w12Efp4w6e1Gdg57A3kcSW8LGmbfKkAFJY7u1pqUJhjT9LbCtvodWVvmYCapC4o-OY5ROa-lhCLWVWmJWkM9xQUeVvJhMxfJVH7dtMiyhB6s8NtIFN4w97beQZ_wpbxWxCtGDzN7i-8NHlG7-H_r-HFfAzBkARkyjtr-_FhtpKN-np7Bi6tzqmcaltPqd4XhcTaw07TmQrtoPcZObOb52uPc5NMFhx20W9IdCaEANXGJ2GB4CEJEVB3AKrmTPs2ETEg3CAOzRqwrQZfjznlsDLzB5LJXzphGePTYsFDmNvZjhhbfv3Hhgg7UjllTZCDzI6B-YlxK1_DrxyN1HPMPi7mLDvXQOkQ-t7otpTorzsTm0dm-zfi1RodWRLrXj0VE8S2tv4oVCi_HS0)
online.


![](/Stdlib/dynamic1.1.png)


```
@startuml
'all sprites in a category would be included in an all.puml file for that category
'==================================================================================================

'create equivalent of icons shown here https://github.com/awslabs/aws-icons-for-plantuml
sprite $Batch [64x64/16z] {
xLQ7bjim30CdzFzVtEV1iErPkJpT7iYm5aWDKERujFZ5Bp8YkSvM011VfMzSDy2Mw1JidbCGAtmllmbPuIkoImjyGUsyBV4LV95_Xny50bpW4uTRAjOKu81b
Xa0vbX3OKFG5C0IMNLyxXA_3PvW5hqHSOFBP_Ovk4036hYi0pJdTCgqD6A0g4FQ0hOwygxSikGOanw11AuvtomxXjNiRDECmn21xxTkJP0N4tdy1Gmu5T2GW
6ygFL_sqbx3NvA_FVtt_ri_F1CZNra-10TpNhvVr2KGcyVCOdoBySlpv-jC1ZSVveO36_Fwb0UASqGqG0QpfJgP2Eo60u59-fLVozhhdNk2WTeDpq2O6AAL_
uV7KGPNO2lya17gz1pMiD1VmFNH9IBLNe3xA3q07eNsMy_WdXESwU4jRmddEk-FUuPFjjthiqAEGVUz8rlqmsK1nhtYlklvp7vWRfka0jUNITUdTzgxFyzLx
-Ikh_YdmYr_y0G
}

'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/ARVR/ARVR.puml
sprite $Arvr [64x64/16z] {
xTG3WiH054NHzutP_th7RHkfsmnEdE1HZMZsIn0_DGDuuVsZJwnMVJ-57txuuKrsP4Tv1mjl3Nw43qZlo147VO9xPueyu8j1l3jm7V0GtPFWe8_UKzpL3rzc
TO4l0gZEzufCsDd-rnhoN2zKtKLoWk-bkHq--vabr0TypEy_WiwEmc9K7FATAd_fVDwOZygdU_uEF_pmLgUMA_wChkV1SavCc4LdXNVe2m
}

'https://github.com/awslabs/aws-icons-for-plantuml/blob/master/dist/ARVR/Sumerian.puml
sprite $Sumerian [64x64/16z] {
xPO5qkim38HN3FU_xuE29mMx-Hbtg4to6GIZxVVJhtvLLI-XbK2QJo6sVv90JA3SImUJRVuAjBeDl8zE0G2EyVy42d87NGOmGG0vVHuu7iRWZt4daBUWWW6j
8w_zNufuHES9KgxpKjr5o6CKQyh5uGi59BTfEuR1GHvEi6cu0N2sWE8sb99j03370L41CkryG9FQh6rTffOJlEWGLz-cbv5N4Pqh83Vf5THL67BA-qXltEu_
2XWrtrzlzZUfwuBCdjy_3ilGeY0Pgmj0NO5ehtb1vh9c0OhsaV_Qfa_hKUzKUDIs_eJgy7myMFEPLzinwd3nSQ0rpwYR_kiWmAgVmezmYuKSJ_94VZJDABad
y4EnAVcdyy4Xo6H_7g-02Se1oIVprMqKX_YdW9_AEtjtdVlNiykVmAS0Tjd_1exTl8wS3Ju5q5sydGux-94Dty4xGtfeyAEewG4FQCvv0vQy0b8zvuiN_EYw
AHy0nu8Ue-gMJrFBOgjTKr_pYfyChlaOjDhmay6vj0xaWvyFxdKOyiYlZSFQGGZIVMbSrhaa46WOf-dmcOS1a3mPjp9mFqqf77FZ-7JZ-Y76UQvV_Uel
}



'=============================DECORATORS==================================
' We define 1 or more sprite decorators in stdlib
' Define our decorators that we know now - and can easily define new ones in future with as manty new parameters 
' as we want, that we don't even know about yet
' Let's say SpriteDecorator is defined month 1, SpriteDecorator2 is defined month 2, SpriteDecorator3 is defined month 3
'---------------------------------------------------
!unquoted procedure $SpriteDecorator($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="red")

rectangle $alias as "
<<$alias>>
$label
<color:$colour><$MySprite*$scale></color>
//<size:12>[$technology]</size>//

  $description"
!endprocedure

'add a new shape parameter
'---------------------------------------------------
!unquoted procedure $SpriteDecorator2($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="green", $shape="node")

$shape $alias as "
<<$alias>>
$label
<color:$colour><$MySprite*$scale></color>
//<size:12>[$technology]</size>//

  $description"
!endprocedure

'add a new shape parameter + a textsize parameter
'---------------------------------------------------
!unquoted procedure $SpriteDecorator3($MySprite, $alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="cloud", $textsize="18")

$shape $alias as "
<<$alias>>
$label
<color:$colour><$MySprite*$scale></color>
//<size:$textsize>[$technology]</size>//

  $description "
!endprocedure

' test STATIC call of decorators with same icon
'---------------------------------------------------
$SpriteDecorator("$Batch", "static_dec1")
$SpriteDecorator2("$Batch", "static_dec2", $shape="node")
$SpriteDecorator3("$Batch", "static_dec3", $shape="cloud", $textsize="20")

' test DYNAMIC call of decorators with same icon
'---------------------------------------------------
'this does not work directly as $SpriteDecorator - so we do indirect as per following line
!$dyn = "$Sprite"+ "Decorator"
%invoke_procedure($dyn, "$Batch", "dynamic_dec1", "description", "label", "technology")

!$dyn2 = "$Sprite"+ "Decorator2"
%invoke_procedure($dyn2, "$Batch", "dynamic_dec2")

!$dyn3 = "$Sprite"+ "Decorator3"
%invoke_procedure($dyn3, "$Batch", "dynamic_dec3")


'=============================END DECORATORS==================================



' The beauty here is that for a given icon, we can change a given macro upwards (but not downwards)
' e.g. can change BATCH_DYN invoked prodedure from $dyn, to $dyn2, to $dyn3 etc...  this gives: 
' future proofing: user's code stays the same, but support for new params can be added
' ability to easily change the default decoration 
!unquoted procedure $BATCH_DYN($alias, $description="", $label="", $technology="", $scale=1, $colour="red")
%invoke_procedure($dyn, "$Batch", $alias, $description, $label, $technology, $scale, $colour)
!endprocedure

!unquoted procedure $ARVR_DYN( $alias, $description="", $label="", $technology="", $scale=1, $colour="green", $shape="node")
%invoke_procedure($dyn2, "$Arvr", $alias, $description, $label, $technology, $scale, $colour, $shape)
!endprocedure

!unquoted procedure $SUMERIAN_DYN($alias, $description="", $label="", $technology="", $scale=1, $colour="blue", $shape="cloud", $textsize="30")
%invoke_procedure($dyn3, "$Sumerian", $alias, $description, $label, $technology, $scale, $colour, $shape, $textsize)
!endprocedure


' User can specify what they want in order, or via named arugments
$BATCH_DYN("batch_dyn_1", "desc", "label", "tech", 1)
$BATCH_DYN("batch_dyn_2", "desc", "label", "tech", 2, "brown")
$BATCH_DYN("batch_dyn_3", $scale=4)

$ARVR_DYN( "arvr_dyn_1")
$ARVR_DYN("arvr_dyn_2", "descsdfsdf", "label", "tech")
$ARVR_DYN( "arvr_dyn_3", $technology="mytech")


$SUMERIAN_DYN("sumerian_dyn_1", "descsdfsdf", "label", "tech")
$SUMERIAN_DYN("sumerian_dyn_2", "descsdfsdf", "label", "tech", 0.5, "pink", "node", 30)



@enduml
```
