# Page View

### 

Fire whenever a user loads a new page, whether done synchronously or asynchronously.

This event should be the first pushed into the data layer on each page. Given many 3rd party scripts push events to the data layer, this event push should be placed in the page `<head>` and should be the first `<script>` tag on the page to ensure it is the first event.

### <ins>_Page Views and Virtual Page Views are now the same in GA4_</ins> 
There is no longer a concept of virtual page view, so this event should be fired whenever a virtual page view would have been fired in the past, such as when a new screen is loaded asynchronously within an angular, react, or vue app/embed.

## Javascript Code
```js
window.dataLayer = window.dataLayer || [];
dataLayer.push({ page_data: null, event_data: null, user_data: null });  // Clear the previous page_data, event_data, and user_data objects.
dataLayer.push({
  event: "page_view",
  detailed_event: "Page View",
  event_data: {
        name: '<name>',
        identifier: "<identifier>"
    },
  page_data: {
        breadcrumb: "<breadcrumb>",
        country: "<country>",
        language: "<language>",
        page_name: "<name>",
        page_location: "<page_location>",
        page_path: "<page_path>",
        page_query_string: "<page_query_string>",
        page_type: "<type>",
        site_section: "<site_section>",
        site_sub_section: "<site_sub_section>",
        site_variant: "<site_variant>",
        community_name: "<community_name>",
        community_id: "<community_id>",
        community_city: "<community_city>",
        community_zip: "<community_zip>",
        community_state: "<community_state>",
        community_rate: "<community_rate>",
        community_service_assisted: "<community_service_assisted>",
        community_service_independent: "<community_service_independent>",
        community_service_short_term: "<community_service_short_term>",
        community_service_hospice: "<community_service_hospice>",
        community_service_memory_care: "<community_service_memory_care>",
        community_service_skilled_nursing: "<community_service_skilled_nursing>",
        community_service_in_home_care: "<community_service_in_home_care>"
    }
});
```

## Variable Definitions

|Path|Type|Required|Description|Example|Max Len|How to test?|
| --- | --- | --- | --- | --- | --- | --- |
|**event_data.name**|`string`|required|The human-readable event name. This should be something that an analyst without a deep knowledge of the technical implementation of the site can easily identify the event with. It should be lowercase snake_case.|`page_view`<br>`add_to_cart`<br>`purchase`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**event_data.identifier**|`string`|required|The machine-readable event identifier. This should be a unique value specific to this piece of content, if one exists. If one does not exist, this can also be populated with the same value as the name param.|`pv_home_1234`<br>`community_92123_ca`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.breadcrumb**|`string`|contextual|A delimited list of hierarchical sections that describe the current page's location within the navigation of the site.|`home\|\|care and living\|\|what is memory care?`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.country**|`string`|required|The country associated with the current page.|`US`<br>`CA`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.language**|`string`|required|The language of the current page, usually pulled from the &lt;html&gt; tag lang attribute.|`en-us`<br>`en-gb`<br>`ch-cn`<br>`fr-ca`<br>`fr-fr`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.page_name**|`string`|required|Captures the name of the page the user is on separate from the title of the page. This should not be pulled from the &&lt;title&gt; tag. |`home`<br>`what is memory care?`<br>`community \| sunrise of dublin`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.page_location**|`string`|required|The URL of the page currently being viewed. This value will include the full, unaltered URL of the page\/screen the user is currently viewing, including query parameters, fragments, etc.|https:\/\/www.example.com\/home?user=true&audience=test\#aboutus|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.page_path**|`string`|required|Captures the path portion of the page URL. This will not include the hostname/domain, query parameters, fragments, etc.|`/`<br>`/communities`<br>`/communities/oh/sunrise-of-dublin`<br>`/care-living/memory-care`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.page_query_string**|`string`|contextual|The query string portion of the URL. This will not include the host name, path, fragments, etc. |`?utm_campaign=example&utm_source=example&utm_medium=example`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.page_type**|`string`|required|Used for grouping pages (or screens) into high level types. Most often aligns with page taxonomy or content type for base page.|`home`<br>`landing page`<br>`information`<br>`lead gen`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.site_section**|`string`|required|The section of the site that the current page resides in.|`home`<br>`communities`<br>`experience sunrise`<br>`care and living`<br>`advice and planning`<br>`search`<br>`etc.`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.site_sub_section**|`string`|contextual|The sub-section of the site that the current page resides in.|`life at sunrise`<br>`pets, our services`<br>`assisted living`<br>`resources`<br>`etc. `|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.site_variant**|`string`|required|Describes the version of the site that is being shown|`responsive`<br>`mobile`<br>`desktop`|`100 (standard), 500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.system_environment**|`string`|required|Describes the specific setup or configuration of an application or system that serves a particular purpose within the development and deployment lifecycle.|`production`<br>`development`<br>`qa`<br>`staging`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_name**|`string`|contextual|The name of the community.|`Shady Pines Retirement Home`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_id**|`string`|contextual|The unique identifier for the community.|`12345`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_city**|`string`|contextual|The city where the community is located.|`Springfield`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_zip**|`string`|contextual|The ZIP code of the community.|`12345`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_state**|`string`|contextual|The state where the community is located.|`IL`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_rate**|`string`|contextual|The rate or cost associated with the community. Often times presented as a "rates starting at $2,000/month".|`2000`|`100 (standard)`<br>`500 (GA360)`|Value not null or empty. Length within limit.|
|**page_data.community_service_assisted**|`string`|contextual|Indicates if assisted living services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_independent**|`string`|contextual|Indicates if independent living services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_short_term**|`string`|contextual|Indicates if short-term stay services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_hospice**|`string`|contextual|Indicates if hospice services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_memory_care**|`string`|contextual|Indicates if memory care services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_skilled_nursing**|`string`|contextual|Indicates if skilled nursing services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
|**page_data.community_service_in_home_care**|`string`|contextual|Indicates if in-home care services are offered at the community. Set to TRUE if the service is offered, FALSE if not offered, and UNDEFINED if the page is not a community-related page.|`TRUE`|`100 (standard)`<br>`500 (GA360)`|Value is either TRUE, FALSE, or UNDEFINED.|
||||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;||&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;|

