#APIM Policy to redirect Http request over to Https

<policies>
<inbound>
  <choose>
    <when condition="@(context.Request.Url.Scheme == "http")">
        <return-response>
          <set-status code="301" />
          <set-header name="Location" exists-action="override">
            <value>@("https" + context.Request.OriginalUrl.ToString().Substring(4))</value>
          </set-header>
        </return-response>
    </when>
</choose>
<base />
</inbound>
<backend>
<base />
</backend>
<outbound>
<base />
</outbound>
<on-error>
<base />
</on-error>
</policies>
