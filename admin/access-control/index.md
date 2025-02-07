---
title: Access control
description: Learn how to change how Coder users sign in.
---

The **Authentication** tab allows you to choose how your users log in and gain
access to Coder. Currently, you can choose between **Built-In Authentication**
and **OpenID Connect**.

## Built-In Authentication

Built-in authentication allows you (or any admin) to manually create users who
log in with their email address and temporary password. Coder will ask them to
change their password after they log in the first time.

## OpenID Connect

The OpenID Connect (OIDC) option allows you to defer identity management to the
OIDC provider of your choice.

### Set up authentication via OIDC

Before proceeding, you'll need to register a Coder application with your OIDC
Provider. You'll need to provide a domain name for the OIDC token callback; use
`https://coder.my-company.com/oidc/callback`.

Once you've done this, you'll need to complete the setup process in Coder. On
the Authentication tab, provide the following parameters:

- **Client ID**: The client ID for the Coder application you registered with the
  OIDC provider
- **Client Secret**: The secret assigned to the Coder application you registered
  with the OIDC provider
- **Issuer** (e.g., `https://my-idp.com/realm/my-org`): The URL where Coder can
  find your OIDC provider's configuration document

If you do not have values for any of these parameters, you can obtain them from
your OIDC provider.

## Disable built-in authentication

You can disable built-in authentication as an option for accessing Coder if you
have OIDC configured.

![Login page with built-in authentication
disabled](../../assets/admin/disable-built-in-auth.png)

To do so, navigate to **Manage** > **Admin** > **Authentication**. Then, toggle
**Disable built-in authentication** to **On** and click **Save preferences**.

[Site managers](user-roles#site-manager-permissions) can still
use built-in authentication. To view this option on the login page, add the
following query parameter to the URL you use to access your Coder deployment:

```text
/login?showAllAuthenticationTypes=1
```

## Change the authentication method

You can change the authentication method by which a user logs into their Coder
account.

To do so, go to **Manage** > **Users**. Find the user whose authentication type
you want to change, and use the **Auth Type** to toggle between **Built-In** and
**OpenID Connect**.
