# BillingApi

All URIs are relative to *https://api.cryptogate.live/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**createBillingCheckout**](BillingApi.md#createBillingCheckout) | **POST** /billing/checkout | Start a plan upgrade or account top-up |


<a id="createBillingCheckout"></a>
# **createBillingCheckout**
> TransactionEnvelope createBillingCheckout(createBillingCheckoutRequest)

Start a plan upgrade or account top-up

### Example
```java
// Import classes:
import live.cryptogate.sdk.ApiClient;
import live.cryptogate.sdk.ApiException;
import live.cryptogate.sdk.Configuration;
import live.cryptogate.sdk.auth.*;
import live.cryptogate.sdk.models.*;
import live.cryptogate.sdk.api.BillingApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.cryptogate.live/v1");
    
    // Configure HTTP bearer authorization: SecretKey
    HttpBearerAuth SecretKey = (HttpBearerAuth) defaultClient.getAuthentication("SecretKey");
    SecretKey.setBearerToken("BEARER TOKEN");

    BillingApi apiInstance = new BillingApi(defaultClient);
    CreateBillingCheckoutRequest createBillingCheckoutRequest = new CreateBillingCheckoutRequest(); // CreateBillingCheckoutRequest | 
    try {
      TransactionEnvelope result = apiInstance.createBillingCheckout(createBillingCheckoutRequest);
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling BillingApi#createBillingCheckout");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters

| Name | Type | Description  | Notes |
|------------- | ------------- | ------------- | -------------|
| **createBillingCheckoutRequest** | [**CreateBillingCheckoutRequest**](CreateBillingCheckoutRequest.md)|  | |

### Return type

[**TransactionEnvelope**](TransactionEnvelope.md)

### Authorization

[SecretKey](../README.md#SecretKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **201** | Billing transaction created. |  -  |
| **401** | Missing or invalid API key (UNAUTHORIZED). |  -  |
| **402** | Merchant platform balance too low for overage fees (INSUFFICIENT_BALANCE). |  -  |
| **403** | Key lacks permission — e.g. a publishable key on a secret-only endpoint, or plan too low (FORBIDDEN, USE_PAY_ENDPOINT, PLAN_UPGRADE_REQUIRED, NO_ACTIVE_PLAN). |  -  |

