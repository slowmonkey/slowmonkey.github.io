---
layout: post
title: "MSAL Angular Setup with HTTP_Interceptor"
categories: [development]
tags: [msal, angular]
---

Setting up MSAL on Angular 8+ applications.

# Introduction

This post describes the steps required to setup MSAL on Angular 8+ using the Microsoft npm package [@azure/msal-angular](https://www.npmjs.com/package/@azure/msal-angular).

https://github.com/AzureAD/microsoft-authentication-library-for-js#readme  
https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-v2-angular  
https://docs.microsoft.com/en-us/azure/active-directory/develop/tutorial-v2-angular  

Authorities:

https://docs.microsoft.com/bs-latn-ba/azure/active-directory/develop/msal-client-application-configuration

The authority is a URL that indicates a directory that MSAL can request tokens from. Common authorities are:

    - https://login.microsoftonline.com/<tenant>/, where <tenant> is the tenant ID of the Azure Active Directory (Azure AD) tenant or a domain associated with this Azure AD tenant. Used only to sign in users of a specific organization.

    - https://login.microsoftonline.com/common/. Used to sign in users with work and school accounts or personal Microsoft accounts.
  
    - https://login.microsoftonline.com/organizations/. Used to sign in users with work and school accounts.
    
    - https://login.microsoftonline.com/consumers/. Used to sign in users with only personal Microsoft accounts (formerly known as Windows Live ID accounts).


Basic Setup

# app.module.ts

Add MsalModule as the last item in the imports section.
Set 
This is required

Add MsalConfig then MsalInteceptor for httpinterception at the top of the providers section.