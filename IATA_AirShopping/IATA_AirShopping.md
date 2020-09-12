# **IATA_AirShopping**


> **Purpose**
>
>The AirShopping transaction set supports both specific and flexible shopping experiences for **anonymous** or personalized shopping. Both functionally-rich attribute shopping and affinity shopping **support date range or specific month (calendar) shopping**, amongst other features.
>
>The response returns Offers which may include branded or itinerary-priced Offers **with or without ancillary Services**. It also returns applicable rules for the integrated prices as well as for each Service. The message also returns **multi-media** content at message level as well as media references at the individual Offer level.




- AirShopping支持匿名的（anonymous）查询服务，是指允许在查询时不提供实际的旅客个人信息。

  目前接触到的多数OOMS中均支持该功能，在发送请求时仅提供旅客类型（如：成人ADT、儿童CHD、婴儿INF等）和对应的数量，即可获取到对应的信息，实际的旅客信息在预订（多数为OrderCreate）时提供。当然这些OOMS在AirShopping的请求中也可以输入旅客个人信息，只是并没有被使用。

  但也有OOMS系统，即不需要输入旅客个人信息，也不需要输入旅客类型和对应的数量。这些系统会在结果中将所有旅客类型的运价信息全部返回。

  针对以上两种做法，更倾向于前者。不需要提供旅客的个人信息，可以尽可能的保护旅客隐私信息，而且这些信息在AirShopping中确实没有起到任何作用。提供旅客的类型和数量，是为了根据旅客类型和数量来判断座位是否能够满足当前需求，并且可以计算出总的运价信息，还可以提供打包运价等。

  

- AirShopping支持基于时间范围（date range or specific month (calendar) ）的查询，是指在查询时不仅可以指定航班的起飞时间，而且可以设置航班的起飞时间在某个跨天的时间范围内。

  目前在作者接触到的范围内并没有发现实现该功能的产品。主要问题应该是对于本身每天存在多个航班的航线，在多段查询时返回结果是每段结果的笛卡尔积，本身返回报文结果巨大，如果支持日历牌查询会使结果指数级增大。对于日历牌查询，可能更适合于不是每天都有航班的航线。

- 附加服务（ancillary Services）基本是各家航司都很关心的点，可以提供包含附加服务和不包含附加服务的运价，其实是需要给出旅客多种选择，标明每段航班支持的附加服务类型以及价格，这里的价格可以是票价与附加服务分离，也可以提供打包票价，这意味着航司可以提供一些优惠来提高附加服务的销量。

- 多媒体（multi-media），目前多数人理解的多媒体内容包括座位图、餐食、附加服务、机上服务等内容的展示，但真正能够完整实现该内容的几乎没有。



> **Features**
>
> | Message  |   Component    |                Features                | 18.2 | Changes |
> | :------: | :------------: | :------------------------------------: | :--: | :-----: |
> | Request  |      Core      |    Search by Origin and Destination    |  ✔   |    -    |
> |          |                |      Search by Affinity Shopping       |  ✔   |    -    |
> |          |                |    Search either side of your query    |  ✔   |    -    |
> |          |                |     Search for specific Flight(s)      |  ✔   |    -    |
> |          |                | Search in context of an existing Order |  ✔   |    -    |
> |          |                |    Search in context of a Passenger    |  ✔   |    -    |
> |          |   Filtering    |               Cabin Type               |  ✔   |    -    |
> |          |                |             Budget Amount              |  ✔   |    -    |
> |          |                |        Maximum Journey Distance        |  ✔   |    -    |
> |          |                |          Keyword Preferences           |  ✔   |    -    |
> |          |                |              Stay Period               |  ✔   |    -    |
> |          |                |             Boarding Gate              |  ✔   |    -    |
> |          |                |              Station Name              |  ✔   |    -    |
> |          |                |             Terminal Name              |  ✔   |    -    |
> |          |                |             Departure Time             |  ✔   |    -    |
> |          |                |          Time before or after          |  ✔   |    -    |
> |          |                |           Alliance Criteria            |  ✔   |    -    |
> |          |                |        Baggage Pricing Criteria        |  ✔   |    -    |
> |          |                |           Carrier Preference           |  ✔   |    -    |
> |          |                |             Fare Criteria              |  ✔   |    -    |
> |          |                |             Aircraft Type              |  ✔   |    -    |
> |          |                |  Flight Characteristics (red eye etc)  |  ✔   |    -    |
> |          |                |          Payment Information           |  ✔   |    -    |
> |          |                |       Frequent Flyer Information       |  ✔   |    -    |
> |          |                |               Promotions               |  ✔   |    -    |
> |          |                |          Seat Characteristics          |  ✔   |    -    |
> |          |                |             Special Needs              |  ✔   |    -    |
> |          |                |              Trip Purpose              |  ✔   |    -    |
> | Response | Carrier Offers |  Summary of Offers (highest, lowest)   |  ✔   |    -    |
> |          |                |           Lowest Offer Price           |  ✔   |    -    |
> |          |                |            A la Carte Offer            |  ✔   |    -    |
> |          |                |             Carrier Offers             |  ✔   |    -    |
> |          |                |             Price Calendar             |  ✔   |    -    |
> |          |     Other      |           Marketing Messages           |  ✔   |    -    |
> |          |                |   Commission applicable to the Agent   |  ✔   |    -    |
> |          |                |             Promotion used             |  ✔   |    -    |
> |          |                |   Policy Information used (PCI, PII)   |  ✔   |    -    |
> |          |                |          Payment Information           |  ✔   |    -    |
> | Message  |    General     |          Multilingual Support          |  ✔   |    -    |
> |          |                |          Inventory Guarantee           |  ✔   |    -    |
> |          |                |             Multi-Currency             |  ✔   |    -    |
> |          |                |           Rich Media Support           |  ✔   |    -    |


