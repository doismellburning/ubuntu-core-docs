---
title: "Secure Brand Store Introduction"
table_of_contents: true
---

## Introduction

A Brand Store provides snaps (via channels) to systems that are configured to



## Ubuntu SSO accounts



You can create an SSO account here: https://login.ubuntu.com/



Note the snap account-id. This is a critical identifier that is used in many

### Brand SSO account




          It is strongly recommended to dedicate the Brand Store SSO account 
          single purpose of Brand activities. It should not be used for
          purposes. It should be considered a critical project asset
          use is strictly limited and controlled. (You can always create
          SSO accounts for these other purposes, although each SSO
          account requires a unique email address.)



- Brand Store administration
- Generating keys used to sign assertions, such as the model and serial
- Gadget snap publishing (if you are using a non-Canonical gadget snap)
- Kernel snap publishing (if you are using a non-Canonical kernel snap)





![image](../../media/brand-store-1.png)

### Brand SSO Keys



[Snapcraft][snapcraft] (the tool used to build snap packages), uses SSO 

!!! Note:

          administer your Brand Store and manage model specific activities 
          as signing the model and uploading the model’s custom gadget snap.
          Using a single Brand SSO account simplifies things and is therefore
          recommended in many situations.

You use a Brand SSO account to create keys used for brand activities:

![image][brand-store-2]

## Assertions

[Assertions][assertions] are signed pieces of information. That is, an

The snap system uses assertions in many places. For example, the model 

## Models

Every system that is connected to a Brand Store contains a signed **model 

!!! Note:
          Any system that does not have a customized model assertion cannot
          a Brand Store. (Classic systems with no custom model assertion now
          have a generic one that points at the Ubuntu Store.)



- The Brand Store it points to
- The model name
- The Brand Store SSO account-id
- The gadget snap name (and on Core systems, the kernel snap)
- And more

As noted, the model assertion is **signed** by a key generated under the Brand

!!! Note:
          As mentioned above, it is strongly recommended to use the Brand 
          SSO account to generate the key that signs the model assertion. This
          document assumes you use the Brand Store SSO account for all such
          purposes.



![image][brand-store-3]

## Systems pointing at the Brand Store

Here we overview what has been discussed so far:

- Systems contain a model assertion.
- The model assertion contains the account-id of the Brand SSO account and
- The model assertion points at the Brand Store.


          This picture still does not show the required system authentication
          through which a system may gain access to their Brand Store.



![image][brand-store-4]

- Models point systems to their Brand Store
- Systems can be rejected by the Brand Store as unauthenticated

## Authentication through the Serial Vault

A normally configured Brand Store authenticates a system trying to access it. 



- The Serial Vault needs to be configured to support the  model. This setup
- The system needs a gadget snap that has a prepare-device hook script that



![image][brand-store-5]

- Gadget points at Serial Vault
- Model points at Brand Store
- Brand Store authenticates system by macaroon
- Snaps are then installed over channels

<!-- LINKS -->

[seeding-a-classic-image]: https://docs.ubuntu.com/core/en/seeding-classic-image
[assertions]: https://docs.ubuntu.com/core/en/reference/assertions
[snapcraft]: https://snapcraft.io
[https://dashboard.snapcraft.io/dev/account/]: https://dashboard.snapcraft.io/dev/account/

<!-- IMAGES -->

[brand-store-1]: ../media/brand-store-1.png
[brand-store-2]: ../media/brand-store-2.png
[brand-store-3]: ../media/brand-store-3.png
[brand-store-4]: ../media/brand-store-4.png
[brand-store-5]: ../media/brand-store-5.png