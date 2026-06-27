# SystemApi

All URIs are relative to *https://api.cryptogate.live/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**getHealth**](SystemApi.md#getHealth) | **GET** /health | API health check |
| [**hostedCheckoutRedirect**](SystemApi.md#hostedCheckoutRedirect) | **GET** /pay | Hosted-checkout redirect (browser flow, publishable key) |


<a id="getHealth"></a>
# **getHealth**
> GetHealth200Response getHealth()

API health check

### Example
```java
// Import classes:
import live.cryptogate.sdk.ApiClient;
import live.cryptogate.sdk.ApiException;
import live.cryptogate.sdk.Configuration;
import live.cryptogate.sdk.models.*;
import live.cryptogate.sdk.api.SystemApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.cryptogate.live/v1");

    SystemApi apiInstance = new SystemApi(defaultClient);
    try {
      GetHealth200Response result = apiInstance.getHealth();
      System.out.println(result);
    } catch (ApiException e) {
      System.err.println("Exception when calling SystemApi#getHealth");
      System.err.println("Status code: " + e.getCode());
      System.err.println("Reason: " + e.getResponseBody());
      System.err.println("Response headers: " + e.getResponseHeaders());
      e.printStackTrace();
    }
  }
}
```

### Parameters
This endpoint does not need any parameter.

### Return type

[**GetHealth200Response**](GetHealth200Response.md)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Service status (intentionally NOT wrapped in the success envelope). |  -  |

<a id="hostedCheckoutRedirect"></a>
# **hostedCheckoutRedirect**
> hostedCheckoutRedirect(pk, amount, crypto, link)

Hosted-checkout redirect (browser flow, publishable key)

Browser-facing redirect to the hosted payment page, authenticated by a **publishable** key in the query string (safe to expose client-side). Not used by the server-side SDKs — included for completeness. 

### Example
```java
// Import classes:
import live.cryptogate.sdk.ApiClient;
import live.cryptogate.sdk.ApiException;
import live.cryptogate.sdk.Configuration;
import live.cryptogate.sdk.models.*;
import live.cryptogate.sdk.api.SystemApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.cryptogate.live/v1");

    SystemApi apiInstance = new SystemApi(defaultClient);
    String pk = "pk_example"; // String | Publishable key, pk_live_… / pk_test_…
    String amount = "amount_example"; // String | Fiat amount (≥ 1.00 USD equivalent).
    CryptoSymbol crypto = CryptoSymbol.fromValue("BTC"); // CryptoSymbol | 
    String link = "link_example"; // String | Payment-link slug for attribution.
    try {
      apiInstance.hostedCheckoutRedirect(pk, amount, crypto, link);
    } catch (ApiException e) {
      System.err.println("Exception when calling SystemApi#hostedCheckoutRedirect");
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
| **pk** | **String**| Publishable key, pk_live_… / pk_test_… | |
| **amount** | **String**| Fiat amount (≥ 1.00 USD equivalent). | |
| **crypto** | [**CryptoSymbol**](.md)|  | [enum: BTC, LTC, DOGE, DASH, ETH, USDT, USDC, DAI, WBTC, SHIB, PEPE, LINK, UNI, AAVE, MKR] |
| **link** | **String**| Payment-link slug for attribution. | [optional] |

### Return type

null (empty response body)

### Authorization

No authorization required

### HTTP request headers

 - **Content-Type**: Not defined
 - **Accept**: application/json

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **302** | Redirect to https://cryptogate.live/transaction/{transaction_id} |  -  |
| **400** | Validation error (INVALID_REQUEST, INVALID_CRYPTO, INVALID_AMOUNT, AMOUNT_TOO_LOW, INVALID_CURRENCY, INVALID_METADATA, WALLET_NOT_CONFIGURED, MISSING_ITEMS, MISSING_ORDER_ID, …). |  -  |

