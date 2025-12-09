# Kubernetes and Azure

> In this section we'll look at a Kubernetes and Azure icon sets
> <https://github.com/dcasati/kubernetes-PlantUML>.
>
> PlantUML will access icon files directly from this repository (it is
> not part of PlantUML Stdlib.)

------------------------------------------------------------------------

## Original

## PlantUML Equivalent

### Play

[<img src="../res/play.png" width="40" alt="playbutton_kub1" />](http://www.plantuml.com/plantuml/uml/bPPHJ-Cu4CVVyocyVTcij903xkcUDWtiWfPZUnHEEWa9JUsXjUhOMNi2z4xttS-9qzOvQ9Nc0UAP_yypiMS6lZW2ItMfaYTZ22txNi_GQYHqRA90qz7zxzU9uw2GbV3AJduv_PMzI46Bn2sbhi12oPJqmAf2LXcrQXQHJnk13YiFHaOBUjaP_VEHvN_N5fCF0fyy75OJdnDR45Nkjoopy78ybxIePxL3ouqcr7JCJPdTIWvMc1k95Qgi9O_Ql7tQcKM5u30xFJh9X7IK91-avgeMM5kr3HEmmfIbqSULD-oJJMLPAVaaKGJf3gtVhQe90vDNrHJji-GOc07868WlzgirWTHeNG0swrkSIqTsTGYylVG1UPu3mGmSTknw-TNOYN4qjpZzu_e0lZ2kDEvyTW0o_QdMbhqKFl-eEcGYAsmgq-q3hWHgahGAICv9FkEvjCZ9x3_F6wGNOtrvpmDwRK2CGO7cQFTnK-IrtGJyZgi_eLQqbo1ZORuk4cLcdM4mqzCd7wD-N_TVP1hOX8A30vBPSWDkUx04HsZVQRz-b8XzB9gjNyCn34JUTEKUxCTqccrDUIK3CfYuqlC3YObPfmLDAR5HgCmH0yS4FflAvKg2IxXH2Zb9enqR5KgY9fPNdP2tQtWhl4HLic81be9muTT1bYXy8aQ6MJbV41FI1cWpSbapSun6JIvvh-PJ0F6PZHvqwtpGmSqs_f5tVlD526hqANb_3AN0hLVbnMqZBa2305RuY3Q6mWX8UVlIHWmsTZxknuZx95tYwhbvYLFqJjPwtt9nLwQWPYtM61_qshmpntZcfEwdQjcBLqAhGJreuLtCaR7eTcmHpw0KX6bKLrbntYNEDiuuxtw3nhTLgBhfgyUngNrmVymy63mS0y4u-iJ-IPX_UcMVzbPzC9zSDNdu31gi_N439ReAE6vZQlVL6aqNMdXj-yhyUuZMFRssIQMUMtJEgtq0zWq8Ns0L1VetsHrg37mP8ZLlUmBvRei-RNnnuf4GOu3uz13ncHSEpFwUfFBAvfTSiUwlh1lq1Gqp-1k2F7p5DY-VsIsgD9erdrbexVp-xjBB6cyxDuBl_vNHk5XTpIq8zEfMtl9H1x9kcpxRXRaTvyMe2JVzwwPOxn1DDAzh-_7oxcuIwnfPw-ag9vR4MstS_OllPnNP-rS-I7RMoOAkp_k1i6EJizuP-PjYwtyotXU72HY52hCY355X-18jgsgt2FJZ_PlZxWkLyi8lg4LTgly0_)
Press to play around with this diagram source online.

I made 1 minor change to the source

1.  Added `` `skinparam linetype polyline ``\` as the "RBAC" text
    overlapped the "Kubernetes Cluster" and polyline generally improves
    layout.



![](/Using%20standard%20library/kubernetes/k1.png)


```
@startuml
footer Kubernetes Plant-UML
scale max 1024 width
skinparam linetype polyline
skinparam nodesep 10
skinparam ranksep 10



' Azure
!define AzurePuml https://raw.githubusercontent.com/RicardoNiepel/Azure-PlantUML/release/2-1/dist

!includeurl AzurePuml/AzureCommon.puml
!includeurl AzurePuml/AzureSimplified.puml

!includeurl AzurePuml/Compute/AzureAppService.puml
!includeurl AzurePuml/Compute/AzureBatch.puml
!includeurl AzurePuml/Containers/AzureContainerRegistry.puml
!includeurl AzurePuml/Containers/AzureKubernetesService.puml
!includeurl AzurePuml/Databases/AzureDatabaseForPostgreSQL.puml
!includeurl AzurePuml/Databases/AzureCosmosDb.puml
!includeurl AzurePuml/Databases/AzureSqlDatabase.puml
!includeurl AzurePuml/DevOps/AzurePipelines.puml
!includeurl AzurePuml/Identity/AzureActiveDirectory.puml
!includeurl AzurePuml/Networking/AzureLoadBalancer.puml
!includeurl AzurePuml/Security/AzureKeyVault.puml
!includeurl AzurePuml/Storage/AzureBlobStorage.puml
!includeurl AzurePuml/Storage/AzureStorage.puml

' Kubernetes
!define KubernetesPuml https://raw.githubusercontent.com/dcasati/kubernetes-PlantUML/master/dist

!includeurl KubernetesPuml/kubernetes_Context.puml
!includeurl KubernetesPuml/kubernetes_Simplified.puml

!includeurl KubernetesPuml/OSS/KubernetesApi.puml
!includeurl KubernetesPuml/OSS/KubernetesIng.puml
!includeurl KubernetesPuml/OSS/KubernetesPod.puml

actor "DevOps" as devopsAlias
collections "Client Apps" as clientalias
collections "Helm Charts" as helmalias

left to right direction

' Azure Components
AzureActiveDirectory(aad, "\nAzure\nActive Directory", "Global")
AzureContainerRegistry(acr, "ACR", "Canada Central")
AzureCosmosDb(cosmos, "\nCosmos DB", "Global")
AzureKeyVault(keyvault, "\nAzure\nKey Vault", "Global")
AzureLoadBalancer(alb, "\nLoad\nBalancer", "Canada Central")
AzureSqlDatabase(sql, "\nExternal\ndata stores", "Canada Central")
AzurePipelines(ado, "CI/CD\nAzure Pipelines", "Global")

' Kubernetes Components
Cluster_Boundary(cluster, "Kubernetes Cluster") {
    KubernetesApi(KubernetesApi, "Kubernetes API", "")
    
    Namespace_Boundary(nsFrontEnd, "Front End") {
        KubernetesIng(ingress, "API Gateway", "")
    }

    Namespace_Boundary(nsBackEnd, "Back End") {
        KubernetesPod(KubernetesBE1, "", "")
        KubernetesPod(KubernetesBE2, "", "")
        KubernetesPod(KubernetesBE3, "", "")
    }

    Namespace_Boundary(nsUtil, "Utiliy Services") {
        KubernetesPod(KubernetesUtil1, "", "")
        KubernetesPod(KubernetesUtil2, "","")
    }
}

Rel(devopsAlias, aad, "AUTH")
Rel(helmalias, KubernetesApi, "helm upgrade")

Rel(aad, keyvault, " ")
Rel(KubernetesApi, aad, "RBAC", "ASYNC")

Rel(clientalias, alb, "HTTP", "ASYNC")
Rel(alb, ingress, "HTTP", "ASYNC")

Rel(ingress, KubernetesBE1, " ")
Rel(KubernetesBE1, KubernetesBE2, " ")
Rel(KubernetesBE1, KubernetesBE3, " ")

Rel(KubernetesBE2, sql, " ")
Rel(KubernetesBE3, keyvault, "Pod Identity")
Rel(KubernetesBE3, cosmos, " ")

Rel(ado, acr, "docker push")
Rel_U(KubernetesApi, acr, "docker pull")
@enduml
```

