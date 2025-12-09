# Using PlantUML Stdlib C4 Lightweight Software Architecture Description Method

## C4

> This section details PlantUML stdlib support for C4.
>
> See `c4-label` for details of C4.

*Big design up front is dumb, but doing no design up front is even
dumber.* Dave Thomas

The [C4 Model](https://c4model.com/) is a lightweight software
architecture description method. It consists of a set of 4 diagrams that
describe the **static** structure of a software system.

Overall, C4 strives for clarity and communication of the story, and
follows [Shneiderman's
mantra](http://www.ifp.illinois.edu/nabhcs/abstracts/shneiderman.html):

> *Overview first, zoom and filter, then details-on-demand*

It is not formal UML e.g. the UML actor stickman is deliberately not
used as it causes confusion between a person or a system.

## C4 PlantUML

[C4-PlantUML](https://github.com/RicardoNiepel/C4-PlantUML) is included
in PlantUML Stdlib. It combines the benefits of
[PlantUML](http://plantuml.com/) and the `c4-label` model for providing
a simple way of describing and communicating software architectures -
especially during up-front design sessions - with an intuitive language
using open source and platform independent tools.

It also supports [C4 PlantUML Snippets for Visual Studio
Code](https://github.com/RicardoNiepel/C4-PlantUML#snippets-for-visual-studio-code)

> <https://github.com/plantuml/plantuml-stdlib/tree/master/C4>

## C4 Example Big Bank

> The examples from
> [C4-PlantUML](https://github.com/RicardoNiepel/C4-PlantUML) are used.
>
> Person sprites are added to the customer box to emphasize the user in
> the diagrams.

### Context

> The top-level diagram shows the big boxes in the system i.e. the
> overall context in which a system operates.
>
> The grey boxes are external i.e. not part of the system we're
> defining.



![](/C4/C4-PlantUML/C4_ContextDiagramSample-bigbankplc.png)



```
@startuml
!include <c4/C4_Context.puml>  

'ref http://plantuml.com/stdlib
!include <office/Users/user.puml>
!include <office/Users/mobile_user.puml>

'LAYOUT_WITH_LEGEND

title System Context diagram for Internet Banking System

Person(customer  , Customer , "<$user> <$mobile_user>\n A customer of the bank, with personal bank accounts" )

System(banking_system, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

System_Ext(mail_system, "E-mail system", "The internal Microsoft Exchange e-mail system.")
System_Ext(mainframe, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(customer, banking_system, "Uses")
Rel_Back(customer, mail_system, "Sends e-mails to")
Rel_Neighbor(banking_system, mail_system, "Sends e-mails", "SMTP")
Rel(banking_system, mainframe, "Uses")
@enduml

```


### Context With More detail

> More detail is then added.



![](/C4/C4-PlantUML/C4_ContextDiagramSample-bigbankplc-landscape.png)



```
@startuml
!include <c4/C4_Context.puml>  

'ref http://plantuml.com/stdlib
!include <office/Users/user.puml>
!include <office/Users/mobile_user.puml>

'LAYOUT_TOP_DOWN
'LAYOUT_AS_SKETCH()
LAYOUT_WITH_LEGEND()

title System Landscape diagram for Big Bank plc

Person(customer  , Customer , "<$user> <$mobile_user>\n A customer of the bank, with personal bank accounts" )

Enterprise_Boundary(c0, "Big Bank plc") {
    System(banking_system, "Internet Banking System", "Allows customers to view information about their bank accounts, and make payments.")

    System_Ext(atm, "ATM", "Allows customers to withdraw cash.")
    System_Ext(mail_system, "E-mail system", "The internal Microsoft Exchange e-mail system.")

    System_Ext(mainframe, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

    Person_Ext(customer_service, "Customer Service Staff", "Customer service staff within the bank.")
    Person_Ext(back_office, "Back Office Staff", "Administration and support staff within the bank.")
}

Rel_Neighbor(customer, banking_system, "Uses")
Rel_R(customer, atm, "Withdraws cash using")
Rel_Back(customer, mail_system, "Sends e-mails to")

Rel_R(customer, customer_service, "Asks questions to", "Telephone")

Rel_D(banking_system, mail_system, "Sends e-mail using")
Rel_R(atm, mainframe, "Uses")
Rel_R(banking_system, mainframe, "Uses")
Rel_D(customer_service, mainframe, "Uses")
Rel_U(back_office, mainframe, "Uses")

Lay_D(atm, banking_system)

Lay_D(atm, customer)
Lay_U(mail_system, customer)
@enduml

```


### Container

> We then drill down into the "Internet Banking" box.



![](/C4/C4-PlantUML/C4_ContainerDiagramSample-bigbankplc.png)



```
@startuml
'!includeurl https://raw.githubusercontent.com/RicardoNiepel/C4-PlantUML/master/C4_Container.puml
!include <c4/C4_Container.puml>  

'ref http://plantuml.com/stdlib
!include <office/Users/user.puml>
!include <office/Users/mobile_user.puml>

LAYOUT_WITH_LEGEND()


title Container diagram for Internet Banking System

Person(customer  , Customer , "<$user> <$mobile_user>\n A customer of the bank, with personal bank accounts" )

System_Boundary(c1, "Internet Banking") {
    Container(web_app, "Web Application", "Java, Spring MVC", "Delivers the static content and the Internet banking SPA")
    Container(spa, "Single-Page App", "JavaScript, Angular", "Provides all the Internet banking functionality to cutomers via their web browser")
    Container(mobile_app, "Mobile App", "C#, Xamarin", "Provides a limited subset of the Internet banking functionality to customers via their mobile device")
    ContainerDb(database, "Database", "SQL Database", "Stores user registraion information, hased auth credentials, access logs, etc.")
    Container(backend_api, "API Application", "Java, Docker Container", "Provides Internet banking functionality via API")
}

System_Ext(email_system, "E-Mail System", "The internal Microsoft Exchange system")
System_Ext(banking_system, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Rel(customer, web_app, "Uses", "HTTPS")
Rel(customer, spa, "Uses", "HTTPS")
Rel(customer, mobile_app, "Uses")

Rel_Neighbor(web_app, spa, "Delivers")
Rel(spa, backend_api, "Uses", "async, JSON/HTTPS")
Rel(mobile_app, backend_api, "Uses", "async, JSON/HTTPS")
Rel_Back_Neighbor(database, backend_api, "Reads from and writes to", "sync, JDBC")

Rel_Back(customer, email_system, "Sends e-mails to")
Rel_Back(email_system, backend_api, "Sends e-mails using", "sync, SMTP")
Rel_Neighbor(backend_api, banking_system, "Uses", "sync/async, XML/HTTPS")


@enduml


```


### Component

> We then drill down into the "API Application" box.



![](/C4/C4-PlantUML/C4_ComponentDiagramSample-bigbankplc.png)



```
@startuml

'!includeurl https://raw.githubusercontent.com/RicardoNiepel/C4-PlantUML/master/C4_Component.puml
!include <c4/C4_Component.puml>  


LAYOUT_WITH_LEGEND()


title Component diagram for Internet Banking System - API Application

Container(spa, "Single Page Application", "javascript and angular", "Provides all the internet banking functionality to customers via their web browser.")
Container(ma, "Mobile App", "Xamarin", "Provides a limited subset ot the internet banking functionality to customers via their mobile mobile device.")
ContainerDb(db, "Database", "Relational Database Schema", "Stores user registration information, hashed authentication credentials, access logs, etc.")
System_Ext(mbs, "Mainframe Banking System", "Stores all of the core banking information about customers, accounts, transactions, etc.")

Container_Boundary(api, "API Application") {
    Component(sign, "Sign In Controller", "MVC Rest Controlle", "Allows users to sign in to the internet banking system")
    Component(accounts, "Accounts Summary Controller", "MVC Rest Controlle", "Provides customers with a summory of their bank accounts")
    Component(security, "Security Component", "Spring Bean", "Provides functionality related to singing in, changing passwords, etc.")
    Component(mbsfacade, "Mainframe Banking System Facade", "Spring Bean", "A facade onto the mainframe banking system.")

    Rel(sign, security, "Uses")
    Rel(accounts, mbsfacade, "Uses")
    Rel(security, db, "Read & write to", "JDBC")
    Rel(mbsfacade, mbs, "Uses", "XML/HTTPS")
}

Rel(spa, sign, "Uses", "JSON/HTTPS")
Rel(spa, accounts, "Uses", "JSON/HTTPS")

Rel(ma, sign, "Uses", "JSON/HTTPS")
Rel(ma, accounts, "Uses", "JSON/HTTPS")
@enduml

```


### Class

> We could then add the Class diagrams for the different Components.
