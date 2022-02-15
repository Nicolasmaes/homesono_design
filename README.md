# HomeSono

## [Training roadmap](https://gitlab.com/ofp-oc-cda2/ressources/-/blob/main/Formation/Programme.md)
## [Directive](https://gitlab.com/ofp-oc-cda2/ressources/-/blob/main/Formation/Fil%20rouge.md#livrables)
#

# Summary

 - [First brainstorm](#first-brainstorm)
 - [Diagrams](#diagrams)
    - [MCD](#mcd)
    -  [MLD](#mld)
    - [Flow Chart](#flow-chart)
# 

 # First brainstorm
- [My project on Notion, easier to read and edit](https://nicolasmaesfr.notion.site/HomeSono-32fc326f03b54eed987b3ba9d79fd54c)
- [the markdown on GitLab](markdown_files/design_first_brainstorm.md)
#

# Diagrams
# MCD
```mermaid
classDiagram

    Users -->  "1..1" Users_roles : has
    Bookings --> "1..*" Products : contains
    Bookings --> "1..1" Users : is made by
    Reviews --> "1..1" Users : is made by
    Users  --> "1..*" Bookings : can make
    Users  --> "1..*" Reviews : can make
    Products "0..*" -->  "1..*" Categories : belongs

    class Users{
        id
        login
        name
        first_name
        email
        password
        gender
        phone_number
        address
        zipcode
        city
        role
    }
    class Products{
        id
        name
        category
        desc
        pictures
        rate
        instructions
        }
    class Categories{
        id
        name
        }
    class Users_roles{
        id
        role
    }
    class Bookings{
        id
        guest_name
        id_product
        pick-up_date
        drop-off_date
        messageFromGuest
        responseFromSeller
        status
    }
    class Reviews{
        id
        guest_name
        id_product
        content
        mark
        verified
    }
```
# 

# MLD
```mermaid
classDiagram

        users_roles  --> users : gets PK from
        users_roles  --> roles : gets PK from
        categories_products  --> products : gets PK from
        categories_products  --> categories : gets PK from
        bookings  --> users : gots PK from
        bookings  --> products : gets PK from
        reviews  --> bookings : gets PK from


    class users{
        USR_ID_USR_PK
        USR_LOGIN_USR
        USR_FIRSTNAME_USR
        USR_EMAIL_USR
        USR_PASSWORD_USR
        USR_GENDER_USR
        USR_PHONENUMBER_USR
        USR_ADDRESS_USR
        USR_ZIPCODE_USR
        USR_CITY_USR
        USR_ROLE_USR
    }
    class roles{
        ROL_ID_ROL_PK
        ROL_ROLE_ROL
    }
    class users_roles{
        URO_ID_USR_FK
        URO_ID_ROL_FK
    }
    class products{
        PRO_ID_PRO_PK
        PRO_NAME_PRO
        PRO_CATEGORY_CPR
        PRO_DESC_PRO
        PRO_PICTURES_PRO
        PRO_RATE_PRO
        PRO_INSTRUCTIONS_PRO
        PRO_ISAVAILABLE_PRO
        }
    class categories{
        CAT_ID_CAT_PK
        CAT_NAME_CAT
        }
    class categories_products{
        CPR_ID_PRO_FK
        CPR_ID_CAT_FK
        }

    class bookings{
        BKG_ID_BKG_PK
        BKG_IDUSER_USR_FK
        BKG_IDPRODUCT_PRO_FK
        BKG_PICKUPDATE_BKG
        BKG_DROPOFFDATE_BKG
        BKG_MESSAGE_BKG
        BKG_RESPONSE_BKG
        BKG_STATUS_BKG
        BKG_ISPROCESSED_BKG
        BKG_CLIENTREACHED_BKG
    }
    class reviews{
        REV_ID_REV_PK
        REV_IDBOOKING_BKG_FK
        REV_CONTENT_REV
        REV_MARK_REV
        REV_VERIFIED_REV
    }
```
#

# Flow Chart
```mermaid
graph TD
    A[USER_VISITOR] --> B(Access the app)
    B --> C[Visit the shop]
    B --> D(Contact the manager)
    B --> E(Access the FAQ section)
    B --> F(Browse product availabilities)
    B --> G(Fill the shopping cart)
    B --> H(Create a user account)
```
```mermaid
graph TD
    A[USER_USER] --> |Log in|B(Access the app)
    B --> C[All privileges from USER_VISITOR]
    B--> M(Access the confirmation/payment section)
    B--> N(Cancel or edit his booking)
    B--> O(Leave review after the rent)
```
```mermaid
graph TD
A[USER_ADMIN]-->|Log in| B(Access the dashboard)
    B--> C(Manage user account)
    B--> D(WRite the FAQ section)
    B--> E(Manage booking requests)
    B--> F(Get message from USERS)
    B--> G(Manage the shop)
```
#

# Other diagrams