### 1. You are planning to add unit tests to your application. You need to be able to assert that published Pub/Sub messages are processed by your subscriber in order. You want the unit tests to be cost-effective and reliable.

What should you do?

- A. Implement a mocking framework.

- B. Create a topic and subscription for each tester.

- C. Add a filter by tester to the subscription.

- D. Use the Pub/Sub emulator.

### Ans: D

Incorrect Answers:

A. Implement a mocking framework.

Implementing a mocking framework is a viable option, but using the Pub/Sub emulator is likely to be simpler and more accurate, as it's specifically designed to mimic Pub/Sub's behavior.

B. Create a topic and subscription for each tester.

Creating a topic and subscription for each tester would involve interacting with the actual Pub/Sub service, which could introduce cost, complexity, and reliability issues into your tests.

C. Add a filter by tester to the subscription.

Adding a filter by tester to the subscription would also involve interacting with the real Pub/Sub service, with the same potential issues as option B.



Correct Answer:

D. Use the Pub/Sub emulator.

Option D, "Use the Pub/Sub emulator," is the most suitable approach here. The Pub/Sub emulator lets you unit-test your code that interacts with Pub/Sub without actually using the real Pub/Sub service. It runs locally and simulates Pub/Sub behavior, which makes your tests faster and doesn't incur any costs.

Links:

https://cloud.google.com/pubsub/docs/emulator


