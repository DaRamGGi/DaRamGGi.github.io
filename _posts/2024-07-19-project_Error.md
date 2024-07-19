```java
Description:

Field shopEntity in com.my.interrior.client.shop.ShopServeice required a bean of type 'com.my.interrior.client.shop.ShopEntity' that could not be found.

The injection point has the following annotations:
	- @org.springframework.beans.factory.annotation.Autowired(required=true)


Action:

Consider defining a bean of type 'com.my.interrior.client.shop.ShopEntity' in your configuration.


```

해당오류는 service쪽에서 entity를 @Autowired로 불러와서 생긴 오류이다.

entity말고 repository를 불러오면된다.