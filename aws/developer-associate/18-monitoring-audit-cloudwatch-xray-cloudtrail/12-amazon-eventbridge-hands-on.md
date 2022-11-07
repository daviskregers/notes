# Amazon EventBridge Hands On

In EventBridge you have EventBuses. There is a Default event bus that Amazon Creates for you and you can use it to define rules for Amazon Services. You can also create custom event buses for your applications.

![](2022-04-26-17-07-05.png)

---

![](2022-04-26-17-07-46.png)

If you need to enable cross account options, you can set up the Resource-based policy as well.

![](2022-04-26-17-08-34.png)

## Events

We have event sources that can come from partners

![](2022-04-26-17-09-22.png)

You can follow the steps on the setup page and you'll have events coming in from the service.

Once we have events, we can set up some rules.

![](2022-04-26-17-10-45.png)

We can select the bus and type (whenever a specific event happens or schedule the rule)

![](2022-04-26-17-11-25.png)

![](2022-04-26-17-12-32.png)

![](2022-04-26-17-13-41.png)

![](2022-04-26-17-15-05.png)

We can have multiple targets for the rule that can be either:
- EventBridge bus
- EventBridge API destination
- Other AWS service.

![](2022-04-26-17-16-23.png)

This will send an email each time an instance is stopped or terminated.

---

We can also access the event archives.

![](2022-04-26-17-17-49.png)

---

We can also replay events.

![](2022-04-26-17-18-14.png)

---

We can also look up event schemas.

![](2022-04-26-17-19-11.png)

![](2022-04-26-17-19-30.png)

You can also download the code bindings for them.

![](2022-04-26-17-20-02.png)