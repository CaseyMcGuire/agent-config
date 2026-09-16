# Method structure example

For example, an order service can coordinate pricing, inventory, payment, and
persistence. In this excerpt, `catalog`, `pricing`, `inventory`, `payments`, and
`orders` are injected dependencies. Transaction and retry handling are omitted
to focus on method structure.

```java
Order placeOrder(Checkout checkout) {
    if (checkout.items().isEmpty()) {
        throw new EmptyOrderException();
    }

    var order = prepareOrder(checkout);
    var reservation = inventory.reserve(order.id(), order.items());
    var authorization = authorizePayment(checkout, order, reservation);

    order.confirm(reservation.id(), authorization.id());
    return orders.save(order);
}

private Order prepareOrder(Checkout checkout) {
    var products = catalog.requireProducts(checkout.productIds());
    var lines = pricing.priceItems(checkout.items(), products);
    var total = pricing.totalIncludingTax(lines, checkout.shippingAddress());

    return Order.pending(checkout.customerId(), lines, total);
}

private PaymentAuthorization authorizePayment(
    Checkout checkout,
    Order order,
    Reservation reservation
) {
    try {
        return payments.authorize(
            order.id(),
            checkout.paymentMethod(),
            order.total()
        );
    } catch (PaymentDeclinedException failure) {
        inventory.release(reservation.id());
        throw failure;
    }
}
```

`prepareOrder` groups product lookup and pricing; `authorizePayment` groups
authorization with the response to a declined payment. The inventory and
repository calls stay visible because their names already express the operations.
