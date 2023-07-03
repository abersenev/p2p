# Overview

Staking API provides seamless integration for initiating staking requests and accessing staking data. By integrating your systems with our validators' infrastructure, you can eliminate the need for dedicated web page forms, making it easier to offer staking services to your customers.

## Key Benefits

- **Reliable Infrastructure**: Gain access to our P2P validator infrastructure, consistently ranked among the top-performing validators, ensuring the reliability and security of your staking operations.

- **Dedicated Support**: Our experienced developers provide customer-oriented support through a dedicated channel, assisting you with any questions or issues during the integration process.

- **Customizable Configuration**: Tailor your staking node by selecting the desired location, MEV relay, and regulatory entity (currently in development). This flexibility allows you to align the staking setup with your specific requirements.

- **Slashing Insurance**: We offer extensive insurance protection against slashing events, with customizable plans to mitigate the risks associated with staking.

To help you get started, refer to the following image illustrating the basic information about interacting with Staking API:

![Staking API Overview](/p2p/intro2.png)

By seamlessly integrating Staking API into your systems, you can enhance your offering and simplify the staking process for your customers.

Staking API is gradually expanding to support close to 50 proof-of-stake protocols, providing you with the ability to stake in all of them. For the list of currently supported networks, visit [Networks Supported](/p2p/staking-platform/networks-supported).

## API Limitations

To ensure optimal usage of Staking API, please be aware of the following limitations:

- **Request Rate Limit**: The API enforces a maximum of 100 requests per minute. Ensure that your application adheres to this limit to avoid disruptions in service.

- **Response Times**: While the P2P infrastructure aims for an average response time of 200 milliseconds (ms), please note that response times may vary depending on the specific nature of the request. P2P guarantees a 95th percentile response time of 10 seconds and a 99th percentile response time of 60 seconds to provide transparency.

By keeping these limitations in mind, you can optimize your usage of Staking API and ensure a smooth and reliable integration process.

If you have any questions or need further assistance, please [contact](/p2p/support/contacts/) us. We are committed to helping you make the most of Staking API and providing a seamless staking experience for your customers.

## What's Next?

- Learn more about [Authentication](/p2p/staking-api/authentication/).
- Refer to [Staking API](/p2p/api/staking-api.html) reference.
- Explore [Examples](/p2p/staking-api/examples/) to learn how to use the API effectively.
