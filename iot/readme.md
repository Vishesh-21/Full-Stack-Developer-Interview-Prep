#### What is IoT?

IoT (Internet of Things) is a network of physical devices embedded with sensors, software, and connectivity to exchange data over the internet without human intervention.These objects collect and exchange data over the internet.

**Characteristics**

- connectivity : Devices are connected to the internet or networks.
- intelligence : Sensors collect data from the environment. Data is processed to make decisions.
- scalability : Supports large numbers of devices.
- dynamic adaptability
- Automation: Minimal human intervention.
- secure challenges

#### Explain the basic components of an IoT system.

- Sensors/Actuators: Collect data and perform actions.

- Devices (Hardware): Microcontrollers like Arduino, Raspberry Pi.

- Connectivity: Wi-Fi, Bluetooth, Zigbee, LoRa.

- Data Processing: Cloud or edge computing.

- User Interface: Mobile apps or web dashboards.

**Name any 4 IoT protocols**
MQTT (Message Queuing Telemetry Transport), CoAP (Constrained Application Protocol), HTTP/REST, Zigbee

#### What is the difference between IoT and M2M?

IoT: Internet-based, large-scale, heterogeneous devices.
M2M: Point-to-point, limited scale, no internet always required.

#### What is an IoT Gateway?

A device/software that connects IoT devices to the cloud/internet, handles protocol translation, and provides security. Most smart devices speak different "languages" (protocols like Bluetooth or Zigbee) that the internet cannot understand directly. The gateway collects data from these devices, translates it, and sends it safely to the internet. It makes the entire IoT system faster, cheaper, and more secure.

**Key Functions**

- Protocol Translation (The Translator)
- Data Filtering and Aggregation
- Security - The gateway acts as a firewall, encrypting the data and protecting the local devices from hackers and cyber-attacks.
- Offline Storage : If the internet connection is lost, the gateway can store the data locally and upload it once the connection is restored, ensuring no data is lost.

#### Applications of IOT

The Internet of Things (IoT) has moved beyond simple gadgets and is now integrated into almost every industry. In simple terms, IoT applications use sensors and the internet to make "dumb" objects "smart" by allowing them to collect data and perform actions automatically. example - smart thermostats, smart lighting, security system, connected applications, Remote Patient Monitoring, fitness wearable etc.

#### What are IoT sensors? Explain any four types.

Sensors detect physical parameters and convert them into signals.
**Types:**

- Temperature Sensor: Measures heat (e.g., LM35).

- Humidity Sensor: Measures moisture in air (e.g., DHT11).

- Motion Sensor: Detects movement (PIR sensor).

- Gas Sensor: Detects gases like LPG, CO (MQ series).

## Explain the role of cloud computing in IoT.

- Massive Data Storage: Acts as an "infinite warehouse" to store the huge amounts of data collected by sensors that have no memory of their own.
- Processing & Analytics: Acts as the "brain" that turns raw numbers into useful information and smart decisions.
- Scalability: Allows you to easily grow from 10 devices to 10,000 without buying new hardware; the cloud just expands to fit.
- Remote Access: Acts as a central hub, allowing you to monitor and control your devices (like a smart camera) from anywhere in the world.
- Enhanced Security: Provides high-level shields (encryption and firewalls) to protect weak IoT devices from being hacked.
- Cost Efficiency: Uses a "pay-as-you-go" model, so you don't waste money building expensive private server rooms.

#### Explain 4 main layers of IOT architecture.

1. Perception Layer (The Senses) : This is the "physical" layer at the bottom. It consists of sensors and actuators that interact with the real world.

2. Network Layer (The Postman) : This layer acts as the bridge that carries the collected data from the device to the internet.

3. Processing Layer (The Brain) : Also called the Middleware Layer, this is where the raw data is analyzed.To store data, filter out noise, and make decisions. It uses Cloud Computing to identify patterns (e.g., "The temperature is too high, send an alert!").

4. Application Layer (The Face) : This is the top layer that the user actually sees and interacts with. It turns the data into readable charts and allows the user to control the devices.

#### What is an IoT protocol? Explain MQTT.

An IoT Protocol is a set of rules that allows different devices to communicate and exchange data.

**MQTT (Message Queuing Telemetry Transport)** is the most popular "language" for IoT. It is a lightweight messaging protocol designed specifically for devices with low power, limited memory, and slow internet connections.Uses publish–subscribe model.Requires low bandwidth.Suitable for real-time IoT applications.Common in smart homes and industrial IoT.

#### Advantages and disadvantages of IOT.

**Advantages**

- Automation: Devices can do repetitive tasks on their own (like a smart vacuum) without you having to do them, which saves human effort.
- Time Saving: You can finish tasks faster.
- Cost Savings: IoT helps save money by being efficient.
- Instant Information: You can access data from anywhere in real-time. You can check your home security camera from your phone even if you are in another city.
- Better Decision Making: Since sensors collect a lot of data, it’s easier to make the right choice.
- Health & Safety

**Disadvantages**

- Security Risks: Because everything is connected to the internet, hackers can potentially break into your system and steal your personal information.
- Privacy Issues: IoT devices collect a lot of personal data.
- Internet Dependency: If your internet goes down or there is a power cut, your "smart" devices might become "dumb" and stop working entirely.
- Complexity: Setting up a network of many different devices can be very difficult and technical for a normal person to manage.

#### What is Edge Computing in IoT?

Processing data near the source (device) instead of sending everything to the cloud to reduce latency and bandwidth.

#### Differentiate between MQTT and CoAP protocols.

| **Parameter**       | **MQTT**                            | **CoAP**                             |
| ------------------- | ----------------------------------- | ------------------------------------ |
| Full Form           | Message Queuing Telemetry Transport | Constrained Application Protocol     |
| Communication Model | Publish–Subscribe                   | Request–Response                     |
| Transport Protocol  | TCP                                 | UDP                                  |
| Architecture        | Broker-based                        | Client–Server                        |
| Overhead            | Very low                            | Low                                  |
| Reliability         | High (uses TCP)                     | Moderate (uses UDP)                  |
| Latency             | Slightly higher                     | Very low                             |
| Power Consumption   | Low                                 | Very low                             |
| Best Use Case       | Continuous data streaming           | REST-based IoT communication         |
| Common Applications | Smart homes, industrial IoT         | Sensor networks, constrained devices |

#### Explain IoT communication models.

IoT communication models define data exchange methods:

1. **Device-to-Device**

   - Devices communicate directly.
   - Example: Bluetooth sensors.

2. **Device-to-Cloud**

   - Devices send data to cloud servers.
   - Example: Smart thermostat.

3. **Device-to-Gateway**

   - Gateway processes data before cloud.
   - Improves security.

4. **Back-End Data Sharing**
   - Data shared between cloud platforms.
   - Useful for analytics and integration.

#### Explain various IoT protocols used at different layers.

- **Application Layer Protocols:** MQTT, CoAP, HTTP.
- **Transport Layer Protocols:** TCP UDP.
- **Network Layer Protocols:** IPv6, 6LoWPAN
- **Data Link Layer Protocols:** Zigbee, bluetooth

#### What is a Smart Thing in IoT?

- A smart thing is a physical object with sensing, processing, and communication capabilities.

- It contains sensors and actuators.

- It uses a microcontroller or microprocessor.

- It can communicate over the internet.

- It operates autonomously or semi-autonomously.

- Example: Smart thermostat, smart watch.

#### What is 6LoWPAN?

Stands for IPv6 over Low-Power Wireless Personal Area Networks. Enables IPv6 on constrained devices.Works with IEEE 802.15.4.

#### What is latency in IoT?

Time delay between data generation and response. Affects real-time applications. Caused by network delays. Reduced using edge computing.

#### Compare cloud computing and edge computing in IoT.

| Parameter          | Cloud Computing | Edge Computing |
| ------------------ | --------------- | -------------- |
| Data Processing    | Centralized     | Decentralized  |
| Latency            | High            | Low            |
| Bandwidth Usage    | High            | Low            |
| Real-Time Response | Limited         | Excellent      |
| Security           | Moderate        | High           |
| Cost               | High            | Lower          |

#### What is an actuator in IoT?

Actuator converts electrical signals into physical action. Works opposite to a sensor. Controlled by microcontroller. Used to move or control mechanisms. Examples: Motor, relay, valve. Used in automation systems.

#### What is device provisioning in IoT?

Process of registering IoT devices.Assigns unique identity to devices.Configures security credentials.Enables device authentication.Required before device deployment.Ensures secure communication.

#### What is OTA (Over-The-Air) update?
Remote firmware update mechanism. No physical access required. Fixes bugs and vulnerabilities. Improves device performance. Saves maintenance cost. Used in large-scale deployments.

#### What is sensor calibration?
Process of adjusting sensor accuracy. Reduces measurement errors. Improves data reliability. Performed periodically. Uses standard reference values. Important for critical applications.