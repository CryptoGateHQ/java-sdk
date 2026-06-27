

# CreateTransactionRequest


## Properties

| Name | Type | Description | Notes |
|------------ | ------------- | ------------- | -------------|
|**crypto** | **CryptoSymbol** |  |  |
|**amount** | **BigDecimal** | Fiat amount (≥ 1.00 USD equivalent). |  |
|**currencyFiat** | **FiatCurrency** |  |  [optional] |
|**metadata** | **Map&lt;String, String&gt;** | Free-form key/value (≤20 keys, string values ≤500 chars, ≤4 KB total). |  [optional] |
|**customerEmail** | **String** |  |  [optional] |
|**successUrl** | **URI** |  |  [optional] |
|**cancelUrl** | **URI** |  |  [optional] |



