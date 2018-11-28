---
description: Learn how to execute a mobile login flow.
toc: true
topics:
  - api-authentication
  - oidc
  - authorization-code
  - pkce
contentType: tutorial
useCase:
  - secure-api
  - call-api
  - add-login
---
# Add Login Using the Mobile Login Flow

<%= include('../../../_includes/_pipeline2') %>

::: note
This tutorial will help you add login to your native/mobile app using the mobile login flow. If you want to learn how the flow works and why you should use it, see [Mobile Login Flow](/flows/concepts/mobile-login-flow).
:::

Auth0 makes it easy for your app to implement the mobile login flow using:

* [Auth0 Mobile SDKs](/libraries): The easiest way to implement the mobile login flow, which will do most of the heavy-lifting for you. Our [Mobile Quickstarts](/quickstart/native) will walk you through the process.
* Authentication API: If you prefer to roll your own, keep reading to learn how to call our API directly.

If you prefer to embed your own login pages within your native/mobile app, you can implement our login widget (Lock UI) directly into your app with our:

* [iOS Lock UI Component library](/libraries/lock-ios/v2)
* [Android Lock UI Component library](/libraries/lock-android/v2)

Following successful login, your application will have access to the user's [ID Token](/tokens/id-token) and [Access Token](/tokens/overview-access-tokens). The ID Token will contain basic user profile information, and the Access Token can be used to call the Auth0 /userinfo endpoint or your own protected APIs.

## Prerequisites

This tutorial can be used to add login to your native/mobile app. If you want to learn to call your API from a native/mobile app, see [Call your API from a Native/Mobile App](/flows/guides/mobile-login-flow/call-api-using-mobile-login-flow).

**Before beginning this tutorial:**

* [Register your Application with Auth0](/applications/native). 
  * Select an **Application Type** of **Native**.
  * Add an **Allowed Callback URL** of **https://${account.namespace}/callback**.
  * Make sure your Application's **[Grant Types](/applications/application-grant-types#how-to-edit-the-application-s-grant_types-property)** include **Authorization Code**.

## Steps

1. [Create a code verifier](#create-a-code-verifier): 
Generate a `code_verifier` that will be sent to Auth0 to request tokens.
2. [Create a code challenge](#create-a-code-challenge): 
Generate a `code_challenge` from the `code_verifier` that will be sent to Auth0 to request an `authorization_code`.
3. [Authorize the user](#authorize-the-user): 
Request the user's authorization and redirect back to your app with an `authorization_code`.
4. [Request Tokens](#request-tokens): 
Exchange your `authorization_code` and `code_verifier` for tokens.
5. [Refresh Tokens](#refresh-tokens):
Use a refresh token to request new tokens.

Optional: [Explore Sample Use Cases](#sample-use-cases)

<%= include('./create-code-verifier') %>

<%= include('./create-code-challenge') %>

<%= include('./authorize-user-add-login') %>

<%= include('./request-tokens') %>

<%= include('./refresh-tokens') %>

<%= include('./sample-use-cases-add-login') %>

## Keep Reading

::: next-steps
- [The OAuth 2.0 protocol](/protocols/oauth2)
- [The OpenID Connect protocol](/protocols/oidc)
- [Tokens used by Auth0](/tokens)
:::