# Service Level Objectives # 

Online services want to ensure customers have a positive experience in their product. One way they do this is by defining **Service Level Objectives**, or **SLOs**.

An SLO is like a guarantee made to customers. By defining an SLO, an organization is promising to maintain a defined level of service, often related to the performance and availability of their systems. Here are some examples:

- The website landing/home page will take <5 seconds to load 99% of the time over a 7 day period
- Checkout service will operate without error 99% of the time each 30 days
- The landing/home page will be able to successfully process at least 1,000 requests per second, 99% of the time, measured in 90-day increments
- Average response time in the cart service is <300 milliseconds, 98% of the time, measured in 7-day increments

Notice each includes the same components:

- **Scope**: The specific area an SLO relates to, such as “checkout service”, or “landing page”. This is an area or function that impacts user experience.
- **Target Value**: A measurable threshold for performance, like “1,000 requests per second” or “less than 5 seconds”. Data used to measure an SLO is referred to as a **Service Level Indicator (SLI)**, because it *indicates* whether an SLO is met.
- **Target Rate**: A percentage of the time performance will meet the target value.
- **Time Window**: Period for which data is evaluated, such as “over 7 days”.

Notice also that each SLO is centered around user experience. SLOs should capture performance and availability levels that, even if *barely* met, would keep the average user satisfied. In the simplest terms:

- **Service *meets* SLO targets → Happy users**
- **Service *misses* SLO targets → Frustrated users**

For this reason, SLOs monitor the performance and availability most likely to impact a user’s experience: like load times, error rates, and functionality working in the manner users need and expect.