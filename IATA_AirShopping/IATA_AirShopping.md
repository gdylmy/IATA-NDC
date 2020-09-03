# **IATA_AirShopping**

------

## Purpose

The AirShopping transaction set supports both specific and flexible shopping experiences for **anonymous** or personalized shopping. Both functionally-rich attribute shopping and affinity shopping **support date range or specific month (calendar) shopping**, amongst other features.

The response returns Offers which may include branded or itinerary-priced Offers with or without ancillary Services. It also returns applicable rules for the integrated prices as well as for each Service. The message also returns multi-media content at message level as well as media references at the individual Offer level.

------



- AirShopping支持匿名的（anonymous）查询服务，是指允许在查询时不提供实际的旅客个人信息。

  ​		目前接触到的多数OOMS中均支持该功能，在发送请求时仅提供旅客类型（如：成人ADT、儿童CHD、婴儿INF等）和对应的数量，即可获取到对应的信息，实际的旅客信息在预订（多数为OrderCreate）时提供。当然这些OOMS在AirShopping的请求中也可以输入旅客个人信息，只是并没有被使用。

  ​		但也有OOMS系统，即不需要输入旅客个人信息，也不需要输入旅客类型和对应的数量。这些系统会在结果中将所有旅客类型的运价信息全部返回。

  ​		针对以上两种做法，更倾向于前者。不需要提供旅客的个人信息，可以尽可能的保护旅客隐私信息，而且这些信息在AirShopping中确实没有起到任何作用。提供旅客的类型和数量，是为了根据旅客类型和数量来判断座位是否能够满足当前需求，并且可以计算出总的运价信息，还可以提供打包运价等。

  

- AirShopping支持基于时间范围（date range or specific month (calendar) ）的查询，是指在查询时不仅可以指定航班的起飞时间，而且可以设置航班的起飞时间在某个跨天的时间范围内。

  ​		目前并没有发现