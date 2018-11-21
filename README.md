# Floom Backend Challenge

Great you're looking to get involved with Floom. Fork this repo, push your solution and add us as a collaborator when you're ready. 

## Brief 

For this task we're gonna build a service that tracks the status of an order from creation to delivery. Notifying the user on status changes and providing an endpoint for the frontend to access providing the current status of a given order. 

##### Driver information

The possible statuses of a consignment are `en_route_to_sender` / `waiting_at_sender` / `en_route_to_recipient` / `delivered` / `unsuccesful`.

The third party delivery provider will send updates to your endpoint of choice. The coordinates correspond to the drivers location. Updates are sent whenever their location or status changes. There's one consignment per order. Each update from the delivery provider has this structure:

```json
{
    "consignmentId":123,
    "coordinates":  [51.5007, 0.1246],
    "status": "en_route"
}
```



##### Order creation

For simplicity let's say we have no in flight orders to begin with. When an order is created on a different service, an endpoint of your choice is called with the following data. From this point onwards you store this order information how you wish, to be served up. 

It's up to you what statuses your service is capable of declaring for an order. If you can produce the logic that generates a given status then add it to a list of potential statuses an order can have. 

```json
{
    "id": 456,
    "userId": 123,
    "consignmentId": 789,
    "delivery_location": [51.5014, 0.1419],
    "sender_location": [51.4839, 0.6044],
    "status": "created"
}
```



##### User notifications

There's no need to implement the notification delivery itself. Create an empty function `sendNotification(userId,orderId,status)` to be called when you would wish to notify the user of a change in order status.


##### Order status endpoint

Create an endpoint that gives an orders current status when called with the orders ID. 


##### Deliverables

Your only framework constraint is that it use Node. Beyond that you can use any library/database you wish or totally vanilla if you fancy, be prepared to discuss your decisions in depth. 

The brief is intentionally open. We don't wish for you to spend more than two hours on the challenge, elaborate on any area of the challenge you wish, so long as the project has the following features:

- An endpoint that accepts the consignment updates
- An endpoint that accepts new orders
- An endpoint that serves an orders current status, provided with the orders ID. 
- A `sendNotification(userId,orderId,status)` function is called when you would like to trigger a notification to the relevant user of the status of their order changing.
