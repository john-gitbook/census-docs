---
description: >-
  This page describes how to configure MySQL credentials for use by Census and
  why those permissions are needed.
---

# MySQL

## Required Permissions <a href="#required-permissions" id="required-permissions"></a>

{% hint style="info" %}
These instructions are well tested to connect Census to MySQL. If you're running into connection issues or missing tables or views, please confirm you've run all of these instructions.
{% endhint %}

Census reads data from one or more tables (possibly across different schemata) in your database and publishes it to the corresponding objects in your destination systems.

We recommend you create a dedicated `CENSUS` user account with a strong, unique password. Census uses this account to connect to your MySQL database. In order for the Census connection to work correctly, the `CENSUS` account must have these permissions:

* Read-only access to any tables and views in any schemata that you would like Census to publish to your destinations.

MySQL permissions are complex and there are many ways to configure access for Census. The script below has been tested with recent MySQL versions and is known to work correctly:

```
-- Create census user the ability to sign in with a password
CREATE USER CENSUS IDENTIFIED BY '<strong, unique password>';

-- GRANT read-only access to which ever schemas you'd like to give access to
GRANT SELECT ON <your schema>.* TO CENSUS;
```

## 💡 Notes <a href="#notes" id="notes"></a>

* Census supports MySQL Community 5.7 or later, as well as recent versions of MariaDB
* If you have multiple schemata that you would like Census to read from, repeat the steps for "\<your schema>" for each of them
* Census supports MySQL with versions TLSv1.2 and greater

## 🚦Allowed IP Addresses <a href="#allowed-ip-addresses" id="allowed-ip-addresses"></a>

If you are restricting access by IP addresses, please add Census's IP addresses to the allowlist in your firewall. You can find Census's set of IP address for your region in [Regions & IP Addresses](../basics/security-and-privacy/regions-and-ip-addresses.md#ip-addresses).
