### Testing in Software Development

Testing is the process of systematically verifying that software behaves as expected, meets requirements, and handles edge cases gracefully. It catches bugs early, prevents regressions, improves code quality, and builds confidence before deployment. In full-stack development, testing spans frontend, backend, databases, and their interactions.

**Level of Testing**

- Unit Testing: Tests individual, isolated units of code (functions, methods, classes).

  - **Goal:** Verify each unit works correctly in isolation.
  - **Tools:** Jest, Mocha (JavaScript); JUnit (Java); Pytest (Python).
  - **Characteristics:** Fast, automated, helps pinpoint bugs precisely.

- Integration Testing: Tests interactions between multiple units or components.

  - **Goal:** Ensure combined parts work together as intended.
  - **Tools:** Postman (APIs); Selenium (UI + backend).
  - **Characteristics:** Slower than unit tests, catches interface issues.

- End-to-End (E2E) Testing: Tests complete user flows from start to finish.

  - **Goal:** Validate the entire application works as a whole.
  - **Tools:** Cypress, Selenium.
  - **Characteristics:** Slowest, most complex, simulates real user behavior.

- Performance Testing: Tests application responsiveness and stability under load.

  - **Goal:** Identify bottlenecks and ensure scalability.
  - **Tools:** JMeter, Locust.
  - **Characteristics:** Focuses on speed, resource usage, and reliability.

**Types of Testing**

- Functional Testing : Verifies specific functionalities against requirements.**Examples:** Unit, Integration, E2E tests.

- Non-Functional Testing : Assesses performance, usability, security, etc.**Examples:** Performance testing, security testing.

**In React :** Jest + RTL Together for testing UI, Together, Jest runs your tests and RTL provides the tools to render and interact with React components. Jest is the executor; RTL is the helper.
| Tool | Purpose |
| ---- | --------------------------------- |
| Jest | Test execution, mocks, assertions |
| RTL | Component rendering & interaction |

**Enzyme vs RTL?**

> Enzyme tests implementation details, while RTL tests user behavior and is the modern recommended approach.
