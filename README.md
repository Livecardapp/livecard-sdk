# LiveCard Tracking API

The LiveCard SDK in your desktop or mobile checkout flow will provide you with a LiveCard ID after successfully uploading a video or gift message. This ID should be passed to your server side processing code that is invoked when a user completes an order. Once a tracking number is generated for this package, you should call the following endpoint to attach tracking information to the LiveCard ID for this order. In this way we will be able to deliver the gift message to the recipient as soon as we have confirmation that the package was delivered.

Method: POST

Endpoint: https://api.live.cards/api/cards/start_tracking

Content-type: multipart/form-data

Parameters:

`card[livecard_id]` _LiveCard ID for this order_

`card[shipping_carrier]` _Carrier code (see list below)_

`card[tracking_number]` _Carrier tracking number for this package_

## Carrier Codes
1. `usps`
2. `ups`
3. `fedex`
4. `dhl_express`

## Response Structure

Response is returned as JSON, following are examples of success and failure responses:

### Success
```
{
    "message": "Tracking for LiveCard id: zLE5UraTotR-gwsWxCWN has been started."
}
```

### Failure
```
{
    "success": false,
    "message": "Card not found",
    "error_code": "1002"
}
```
