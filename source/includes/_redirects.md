# Booking Redirects

In addition to price information, your users will need a url that redirects them to where they can book their ticket. 

You can either:

* redirect your users to the Skyscanner website 
* redirect them directly to the supplier's website (airline or travel agent)

<aside class="notice" >
  We recommend that you redirect users to Skyscanner's website as this helps with trust and therefore will enhance your conversion rate. For more information please see <a href="#improving-your-conversions">improving your conversions</a>

</aside>

## To Skyscanner

Link to the Skyscanner website with the details of the search query pre-populated. This provides a more straightforward option for partners who do not require a full implementation of a travel search product within their applications.

If the query isn't specific enough to link to a specific 'day view' page, it will link to a more general browse page, where the user will be asked to refine the search criteria (by date, origin and/or destination).


```shell
GET "http://partners.api.skyscanner.net/apiservices/
    referral/v1.0/{country}/{currency}/{locale}/
    {originPlace}/{destinationPlace}/
    {outboundPartialDate}/{inboundPartialDate}
    ?apiKey={shortApiKey}"
```
*API endpoint*

`/referral/v1.0/{country}/{currency}/{locale}/{originPlace}/{destinationPlace}/{outboundPartialDate}/{inboundPartialDate}`

*REQUEST PARAMETERS*

Parameter | Description |
--------- | ------- |
| ```country``` <br><span class="required">REQUIRED</span> | The [market country](#markets) your user is in |
| ```currency``` <br><span class="required">REQUIRED</span> | The [currency](#currencies) you want the prices in |
| ```locale``` <br><span class="required">REQUIRED</span> | The [locale](#locales) you want the results in (ISO locale) |
| ```originPlace``` <br><span class="required">REQUIRED</span> | The origin place (see [places](#places)) |
| ```destinationPlace``` <br><span class="required">REQUIRED</span> | The destination place (see [places](#places)) |
| ```outboundPartialDate``` <br><span class="required">REQUIRED</span> | The outbound date. Format "yyyy-mm-dd", "yyyy-mm" or "anytime". |
| ```inboundPartialDate``` <br><span class="optional">OPTIONAL</span> | The return date. Format "yyyy-mm-dd", "yyyy-mm" or "anytime". Use empty string for oneway trip. |
```shortApiKey``` <br><span class="required">REQUIRED</span> | The first 16 characters of your API Key |


<aside class="warning">
  Please insure that you use the short API key (the first 16 characters of your full API key) to avoid exposing your key. Please see <a href="#authentication">authentication</a> for more information.

</aside>

*EXAMPLE REDIRECT*

<a href="http://partners.api.skyscanner.net/apiservices/referral/v1.0/GB/GBP/en-GB/EDI/CDG/2014-12-12/2014-12-20?apiKey=prtl674938798674" target="_blank">http://partners.api.skyscanner.net/apiservices/referral/v1.0/GB/GBP/en-GB/EDI/CDG/2017-12-12/2017-12-20?apiKey=prtl674938798674</a>



## To the supplier


When using [flights live prices](#flights-live-prices) or [car hire live prices](#car-hire-live-prices), urls or deeplinks will be provided in the response. They will link the user straight through to the supplier's website.

The URL is an unbranded version of Skyscanner’s own deeplinking service that redirects users to the third-party supplier's website, with the details of the itinerary that was selected. 

![deeplink page](/images/deeplink.png)


You can customise the redirect page by replacing the default logo with the logo of your website. Please send us a logo in size 122x65px in PNG format and we will set this up for you. 

<aside class="warning">
Skyscanner has no control over how the third-party website consumes the link. In some cases the selected itinerary will be ready to book. In other cases the search criteria will be pre-populated, but the end-user will have to search through the results on the third-party website to find their itinerary.
</aside>