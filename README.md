PayPay SDK JAVA

[![License](https://img.shields.io/:license-apache-orange.svg)](https://opensource.org/licenses/Apache-2.0)
[![Coverage Status](https://coveralls.io/repos/github/paypay/paypayopa-sdk-java/badge.svg?branch=master)](https://coveralls.io/github/paypay/paypayopa-sdk-java?branch=master)
[![Language grade: Java](https://img.shields.io/lgtm/grade/java/g/paypay/paypayopa-sdk-java.svg?logo=lgtm&logoWidth=18)](https://lgtm.com/projects/g/paypay/paypayopa-sdk-java/context:java)

Java SDK for interacting with the Paypay APIs
This is the quickest way to integrate PayPay payment services. This is primarily meant for merchants who wish to perform interactions with the Paypay API programatically.
With PayPay's OPA SDK, you can build a custom Payment checkout process to suit your unique business needs and branding guidelines.
## Integrating with PayPay OPA
## Prerequisites
Before integrating with the SDK, run through this checklist:
- [*] Understand the payment flow
- [*] Sign up for a PayPay developer/merchant Account
- [*] Generate the API keys from the Developer Panel. Use the sandbox API Keys to test out the integration
## HMAC Signature Verification
Signature verification is a mandatory step to ensure that the callback is sent by PayPay and the payment is received from an authentic source.
### Generate a Signature
The PayPay signature, returned to you by the Checkout form on successful payment, can be regenerated by your system and verified as follows:
Step 1: Hash the body and content-type with MD5 algorithm
Note : If there is no request body, for instance, the HTTP GET method case, no need of generating MD5. Instead hash value is set as "empty".
The value of authHeader is passed in HttpHeader.AUTHORIZATION. With the authHeader will decode back the data added and with the HTTP request object and based on data available for api-key in the system, 
we will recreate the SHA256("key", requestParams) which gives macData. This macData is verified against the value passed in the header.
Note: Hmac authorization will be done internally by the SDK, the client need not worry about it.

## Requirements

Building the API client library requires Gradle to be installed.

## Installation

To install the API client library to your local Maven repository, simply execute:


Add this dependency to your project's build file:

```groovy
compile "jp.ne.paypay:paypayopa:0.1"
```

## Getting Started

Please follow the [installation](#installation) instruction and execute the following Java code:

```
Please refer jp.ne.paypay.example.PaymentApiExample.java for usage of APIs

```

You need to setup your key and secret using the following:

```java
    ApiClient apiClient = new Configuration().getDefaultApiClient();
    apiClient.setProductionMode(false); //true for production and false for sandbox. Default is sandbox
    apiClient.setApiKey("YOUR_API_KEY");
    apiClient.setApiSecretKey("YOUR_API_SECRET");
    apiClient.setAssumeMerchant("YOUR_MERCHANT_KEY");
```
## Documentation for API Endpoints

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*PaymentApi* | [**createAccountLinkQRCode**](docs/PaymentApi.md#createAccountLinkQRCode) | **POST** /v1/qr/sessions | Create an ACCOUNT LINK QR and display it to the user
*PaymentApi* | [**cancelPayment**](docs/PaymentApi.md#cancelPayment) | **DELETE** /v1/payments/{merchantPaymentId} | Cancel a payment
*PaymentApi* | [**capturePaymentAuth**](docs/PaymentApi.md#capturePaymentAuth) | **POST** /v1/payments/capture | Capture a payment authorization
*PaymentApi* | [**createPayment**](docs/PaymentApi.md#createPayment) | **POST** /v1/payments | Create a payment
*PaymentApi* | [**createQRCode**](docs/PaymentApi.md#createQRCode) | **POST** /v1/codes | Create a Code
*PaymentApi* | [**deleteQRCode**](docs/PaymentApi.md#deleteQRCode) | **DELETE** /v1/codes/{codeId} | Delete a Code
*PaymentApi* | [**getPaymentDetails**](docs/PaymentApi.md#getPaymentDetails) | **GET** /v1/payments/{merchantPaymentId} | Get payment details
*PaymentApi* | [**getRefundDetails**](docs/PaymentApi.md#getRefundDetails) | **GET** /v1/refunds/{merchantRefundId} | Get refund details
*PaymentApi* | [**refundPayment**](docs/PaymentApi.md#refundPayment) | **POST** /v1/refunds | Refund a payment
*WalletApi* | [**checkWalletBalance**](docs/WalletApi.md#checkWalletBalance) | **GET** /v1/wallet/check_balance | Check user wallet balance
*UserApi* | [**getMaskedUserProfile**](docs/UserApi.md#getMaskedUserProfile) | **GET** /v1/user/profile/secure?userAuthorizationId&#x3D;{userAuthorizationId} | Get masked user profile
*UserApi* | [**getUserAuthorizationStatus**](docs/UserApi.md#getUserAuthorizationStatus) | **GET** /v1/user/authorizations?userAuthorizationId&#x3D;{userAuthorizationId} | Get user authorization status
*UserApi* | [**unlinkUser**](docs/UserApi.md#unlinkUser) | **DELETE** /v1/user/authorizations/{userAuthorizationId} | Unlink user

## Documentation for Models

 - [Capture](docs/Capture.md)
 - [CaptureObject](docs/CaptureObject.md)
 - [PaymentDetails](docs/PaymentDetails.md)
 - [RefundDetails](docs/RefundDetails.md)
 - [WalletBalance](docs/WalletBalance.md)
 - [BalanceData](docs/BalanceData.md)
 - [QRCodeDetails](docs/QRCodeDetails.md)
 - [MerchantOrderItem](docs/MerchantOrderItem.md)
 - [MerchantOrderItemResponse](docs/MerchantOrderItemResponse.md)
 - [MoneyAmount](docs/MoneyAmount.md)
 - [NotDataResponse](docs/NotDataResponse.md)
 - [Payment](docs/Payment.md)
 - [PaymentDetails](docs/PaymentDetails.md)
 - [PaymentMethodDetails](docs/PaymentMethodDetails.md)
 - [PaymentMethodListDetails](docs/PaymentMethodListDetails.md)
 - [PaymentOrder](docs/PaymentOrder.md)
 - [PaymentOrderDetails](docs/PaymentOrderDetails.md)
 - [PaymentState](docs/PaymentState.md)
 - [PaymentStateCaptures](docs/PaymentStateCaptures.md)
 - [PaymentStateRefunds](docs/PaymentStateRefunds.md)
 - [PaymentStateRevert](docs/PaymentStateRevert.md)
 - [ProductType](docs/ProductType.md)
 - [QRCode](docs/QRCode.md)
 - [QRCodeResponse](docs/QRCodeResponse.md)
 - [Refund](docs/Refund.md)
 - [RefundOrder](docs/RefundOrder.md)
 - [RefundState](docs/RefundState.md)
 - [ResultInfo](docs/ResultInfo.md)
 - [AccountLinkQRCode](docs/AccountLinkQRCode.md)
