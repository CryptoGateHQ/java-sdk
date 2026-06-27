# DefaultApi

All URIs are relative to *https://api.cryptogate.live/v1*

| Method | HTTP request | Description |
|------------- | ------------- | -------------|
| [**paymentWebhook**](DefaultApi.md#paymentWebhook) | **POST** /paymentEvent | Payment lifecycle event delivered to the merchant&#39;s webhook URL |


<a id="paymentWebhook"></a>
# **paymentWebhook**
> paymentWebhook(webhookPayload)

Payment lifecycle event delivered to the merchant&#39;s webhook URL

Signed with HMAC-SHA256 over the RAW request body. Verify by comparing &#x60;X-CryptoGate-Signature: sha256&#x3D;&lt;hex&gt;&#x60; to &#x60;hex(hmac_sha256(webhook_secret, raw_body))&#x60; using a constant-time compare. Also sent: &#x60;X-CryptoGate-Event&#x60; (the event type) and &#x60;X-Webhook-ID&#x60; (unique delivery id — use for idempotency). 

### Example
```java
// Import classes:
import live.cryptogate.sdk.ApiClient;
import live.cryptogate.sdk.ApiException;
import live.cryptogate.sdk.Configuration;
import live.cryptogate.sdk.auth.*;
import live.cryptogate.sdk.models.*;
import live.cryptogate.sdk.api.DefaultApi;

public class Example {
  public static void main(String[] args) {
    ApiClient defaultClient = Configuration.getDefaultApiClient();
    defaultClient.setBasePath("https://api.cryptogate.live/v1");
    
    // Configure HTTP bearer authorization: SecretKey
    HttpBearerAuth SecretKey = (HttpBearerAuth) defaultClient.getAuthentication("SecretKey");
    SecretKey.setBearerToken("BEARER TOKEN");

    DefaultApi apiInstance = new DefaultApi(defaultClient);
    WebhookPayload webhookPayload = new WebhookPayload(); // WebhookPayload | 
    try {
      apiInstance.paymentWebhook(webhookPayload);
    } catch (ApiException e) {
      System.err.println("Exception when calling DefaultApi#paymentWebhook");
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
| **webhookPayload** | [**WebhookPayload**](WebhookPayload.md)|  | [optional] |

### Return type

null (empty response body)

### Authorization

[SecretKey](../README.md#SecretKey)

### HTTP request headers

 - **Content-Type**: application/json
 - **Accept**: Not defined

### HTTP response details
| Status code | Description | Response headers |
|-------------|-------------|------------------|
| **200** | Acknowledge within 15s. Non-2xx is retried with backoff. |  -  |

