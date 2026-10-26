# Requirements Document

## Introduction

Este documento especifica los requisitos para un tutorial completo e interactivo de IoT con AWS diseñado para principiantes. El tutorial proporciona contenido teórico, simuladores de dispositivos IoT en Python, un dashboard web para visualización de datos, y laboratorios prácticos paso a paso. El sistema no requiere hardware físico, utilizando simuladores para enseñar conceptos de IoT, AWS IoT Core, protocolos MQTT, seguridad, y patrones comunes de arquitectura.

## Glossary

- **Tutorial_System**: El sistema completo de tutorial interactivo de IoT con AWS
- **Device_Simulator**: Componente Python que simula dispositivos IoT enviando telemetría y recibiendo comandos
- **Dashboard**: Interfaz web para visualizar datos de sensores y controlar dispositivos
- **Lab_Module**: Unidad independiente de aprendizaje práctico con instrucciones paso a paso
- **Content_Manager**: Componente que gestiona y presenta el contenido teórico
- **MQTT_Client**: Cliente que maneja comunicación MQTT con AWS IoT Core
- **Telemetry_Data**: Datos de sensores (temperatura, humedad, presión)
- **AWS_IoT_Core**: Servicio AWS para gestión de dispositivos IoT
- **Certificate**: Certificado X.509 para autenticación de dispositivos
- **Thing**: Representación virtual de un dispositivo IoT en AWS IoT Core
- **Topic**: Canal de comunicación MQTT para publicar/suscribirse a mensajes
- **IoT_Rule**: Regla de AWS IoT Core para procesar y enrutar mensajes
- **Device_Shadow**: Documento JSON que almacena el estado actual y deseado de un dispositivo
- **Configuration_File**: Archivo con parámetros de configuración para conexión AWS
- **Error_Handler**: Componente que gestiona errores y proporciona información de troubleshooting
- **Setup_Guide**: Documentación paso a paso para configurar AWS IoT Core
- **Architecture_Diagram**: Representación visual de la arquitectura del sistema
- **Learning_Path**: Secuencia progresiva de contenido de simple a complejo
- **Beginner_User**: Usuario con conocimientos básicos de programación pero sin experiencia en IoT

## Requirements

### Requirement 1: Content Delivery System

**User Story:** As a Beginner_User, I want to access progressive theoretical content, so that I can learn IoT concepts from basic to advanced levels.

#### Acceptance Criteria

1. THE Content_Manager SHALL provide theoretical content organized in a Learning_Path from basic to advanced topics
2. THE Content_Manager SHALL include explanations of IoT fundamentals including device architecture, connectivity, and data flow
3. THE Content_Manager SHALL include explanations of AWS IoT Core concepts including Things, Topics, IoT_Rules, and Device_Shadow
4. THE Content_Manager SHALL include explanations of MQTT, HTTP, and WebSocket protocols with usage examples
5. THE Content_Manager SHALL include explanations of IoT security concepts including Certificates, policies, and authentication mechanisms
6. THE Content_Manager SHALL include best practices and common architectural patterns for IoT solutions
7. THE Content_Manager SHALL include Architecture_Diagrams for each major concept showing component relationships

### Requirement 2: Device Simulation Capabilities

**User Story:** As a Beginner_User, I want to run a simulated IoT device on my computer, so that I can learn IoT concepts without physical hardware.

#### Acceptance Criteria

1. THE Device_Simulator SHALL generate simulated Telemetry_Data for temperature sensors with values between -20 and 50 degrees Celsius
2. THE Device_Simulator SHALL generate simulated Telemetry_Data for humidity sensors with values between 0 and 100 percent
3. THE Device_Simulator SHALL generate simulated Telemetry_Data for pressure sensors with values between 950 and 1050 hPa
4. WHEN configured with a transmission interval, THE Device_Simulator SHALL publish Telemetry_Data at the specified interval
5. WHEN connected to AWS_IoT_Core, THE Device_Simulator SHALL use the MQTT_Client to publish Telemetry_Data to configured Topics
6. WHEN a command message is received on a subscribed Topic, THE Device_Simulator SHALL process the command and update its behavior accordingly
7. THE Device_Simulator SHALL accept Configuration_Files containing AWS endpoint, Certificate paths, and Thing name
8. THE Device_Simulator SHALL support Python 3.10 or higher runtime environments

### Requirement 3: AWS IoT Core Connectivity

**User Story:** As a Beginner_User, I want the simulator to connect securely to AWS IoT Core, so that I can experience real cloud IoT communication.

#### Acceptance Criteria

1. WHEN provided with valid Certificates and AWS endpoint, THE MQTT_Client SHALL establish a secure TLS connection to AWS_IoT_Core
2. WHEN connection fails, THE MQTT_Client SHALL retry connection with exponential backoff up to 5 attempts
3. WHEN disconnected unexpectedly, THE MQTT_Client SHALL automatically attempt to reconnect within 10 seconds
4. THE MQTT_Client SHALL authenticate using X.509 Certificates provided in the Configuration_File
5. WHEN publishing messages, THE MQTT_Client SHALL use Quality of Service level 1 to ensure at-least-once delivery
6. THE MQTT_Client SHALL subscribe to command Topics specified in the Configuration_File upon successful connection
7. WHEN a connection error occurs, THE Error_Handler SHALL log the error with descriptive troubleshooting information

### Requirement 4: Data Visualization Dashboard

**User Story:** As a Beginner_User, I want to see real-time sensor data in a web dashboard, so that I can visualize the data flowing from my simulated devices.

#### Acceptance Criteria

1. THE Dashboard SHALL display current Telemetry_Data values for temperature, humidity, and pressure in real-time with updates every 2 seconds or less
2. THE Dashboard SHALL display historical Telemetry_Data in line charts showing the last 50 data points
3. THE Dashboard SHALL provide controls to send commands to connected Device_Simulator instances
4. THE Dashboard SHALL display the connection status of each registered Thing
5. THE Dashboard SHALL use HTML, CSS, and JavaScript for the frontend interface
6. WHEN Telemetry_Data is received, THE Dashboard SHALL update visualizations without requiring page refresh
7. THE Dashboard SHALL be accessible through a web browser on localhost

### Requirement 5: Laboratory Modules Structure

**User Story:** As a Beginner_User, I want to complete hands-on labs step by step, so that I can practice IoT concepts in a structured way.

#### Acceptance Criteria

1. THE Tutorial_System SHALL provide Lab_Module 1 covering AWS IoT Core setup including account configuration and service access
2. THE Tutorial_System SHALL provide Lab_Module 2 covering creation of a Thing, Certificate generation, and policy attachment
3. THE Tutorial_System SHALL provide Lab_Module 3 covering running the Device_Simulator and publishing MQTT messages to AWS_IoT_Core
4. THE Tutorial_System SHALL provide Lab_Module 4 covering creation of IoT_Rules to process incoming Telemetry_Data
5. THE Tutorial_System SHALL provide Lab_Module 5 covering integration with DynamoDB to store Telemetry_Data
6. THE Tutorial_System SHALL provide Lab_Module 6 covering deployment and configuration of the Dashboard
7. THE Lab_Module SHALL be executable independently without requiring completion of previous Lab_Modules
8. THE Lab_Module SHALL include step-by-step instructions with expected outputs for verification

### Requirement 6: AWS Configuration Documentation

**User Story:** As a Beginner_User, I want detailed AWS setup instructions, so that I can configure AWS IoT Core even without prior AWS experience.

#### Acceptance Criteria

1. THE Setup_Guide SHALL provide step-by-step instructions for creating an AWS account
2. THE Setup_Guide SHALL provide step-by-step instructions for accessing AWS IoT Core service through the AWS Console
3. THE Setup_Guide SHALL provide step-by-step instructions for creating a Thing in AWS_IoT_Core with screenshots
4. THE Setup_Guide SHALL provide step-by-step instructions for generating and downloading Certificates
5. THE Setup_Guide SHALL provide step-by-step instructions for creating and attaching IoT policies to Certificates
6. THE Setup_Guide SHALL provide step-by-step instructions for configuring IoT_Rules for data processing
7. THE Setup_Guide SHALL provide step-by-step instructions for setting up DynamoDB tables for data storage
8. THE Setup_Guide SHALL include troubleshooting guidance for common configuration errors

### Requirement 7: Code Documentation Standards

**User Story:** As a Beginner_User, I want well-documented code, so that I can understand how each component works and learn from the examples.

#### Acceptance Criteria

1. THE Tutorial_System SHALL include inline comments explaining the purpose of each function and class
2. THE Tutorial_System SHALL include docstrings for all public functions describing parameters, return values, and exceptions
3. THE Tutorial_System SHALL include README files in each Lab_Module directory explaining the lab objectives and execution steps
4. THE Tutorial_System SHALL include code examples demonstrating each major concept with explanatory comments
5. THE Tutorial_System SHALL follow PEP 8 style guidelines for Python code consistency
6. THE Tutorial_System SHALL include variable and function names that clearly indicate their purpose
7. THE Tutorial_System SHALL include a main README file with project overview, installation instructions, and prerequisites

### Requirement 8: Error Handling and Troubleshooting

**User Story:** As a Beginner_User, I want helpful error messages and troubleshooting guides, so that I can resolve problems independently.

#### Acceptance Criteria

1. WHEN an AWS connection error occurs, THE Error_Handler SHALL display a message indicating the connection failure with possible causes
2. WHEN Certificate authentication fails, THE Error_Handler SHALL display a message indicating certificate issues with validation steps
3. WHEN MQTT publishing fails, THE Error_Handler SHALL display a message indicating the specific failure reason and retry status
4. WHEN Configuration_File is missing or invalid, THE Error_Handler SHALL display a message listing required configuration parameters
5. WHEN Python dependencies are missing, THE Tutorial_System SHALL display a message with installation commands
6. THE Tutorial_System SHALL include a troubleshooting section documenting common errors and their solutions
7. THE Tutorial_System SHALL log all errors to a log file with timestamps and detailed context information

### Requirement 9: Parser and Serializer Requirements for Configuration

**User Story:** As a Beginner_User, I want configuration files to be validated correctly, so that I can identify configuration errors before runtime.

#### Acceptance Criteria

1. WHEN a Configuration_File is provided, THE Config_Parser SHALL parse JSON or YAML format into configuration objects
2. WHEN a Configuration_File contains invalid syntax, THE Config_Parser SHALL return a descriptive error message indicating the line and issue
3. THE Config_Formatter SHALL format configuration objects back into valid JSON or YAML files
4. FOR ALL valid configuration objects, parsing then formatting then parsing SHALL produce an equivalent configuration object

### Requirement 10: Data Processing and Storage

**User Story:** As a Beginner_User, I want to learn how to process and store IoT data, so that I can build real-world IoT applications.

#### Acceptance Criteria

1. WHEN Telemetry_Data is published to AWS_IoT_Core, THE IoT_Rule SHALL evaluate the message against configured conditions
2. WHEN an IoT_Rule condition matches, THE IoT_Rule SHALL execute the configured action within 1 second
3. THE IoT_Rule SHALL support actions to store Telemetry_Data in DynamoDB tables
4. THE IoT_Rule SHALL support actions to forward Telemetry_Data to other AWS services
5. WHEN Telemetry_Data is stored in DynamoDB, THE Tutorial_System SHALL include the timestamp, device identifier, and all sensor values
6. THE Tutorial_System SHALL provide example queries to retrieve stored Telemetry_Data from DynamoDB
7. THE Tutorial_System SHALL include Lab_Module examples demonstrating data transformation using IoT_Rules

### Requirement 11: Command and Control Functionality

**User Story:** As a Beginner_User, I want to send commands to my simulated device, so that I can learn bidirectional IoT communication.

#### Acceptance Criteria

1. WHEN a command is sent from the Dashboard, THE Dashboard SHALL publish the command message to the device's command Topic
2. WHEN the Device_Simulator receives a command to change transmission interval, THE Device_Simulator SHALL update its interval to the specified value within 5 seconds
3. WHEN the Device_Simulator receives a command to enable or disable a sensor, THE Device_Simulator SHALL update its publishing behavior accordingly
4. WHEN the Device_Simulator receives a command to reset sensor values, THE Device_Simulator SHALL reinitialize sensor readings
5. THE Device_Simulator SHALL acknowledge received commands by publishing a confirmation message to a response Topic
6. THE Dashboard SHALL display command acknowledgment status within 3 seconds of sending
7. WHEN an invalid command is received, THE Device_Simulator SHALL publish an error message indicating the command was not recognized

### Requirement 12: Device Shadow Integration

**User Story:** As a Beginner_User, I want to learn about device shadows, so that I can understand state synchronization in IoT.

#### Acceptance Criteria

1. WHEN the Device_Simulator starts, THE Device_Simulator SHALL report its current state to its Device_Shadow
2. WHEN the Device_Shadow desired state is updated, THE Device_Simulator SHALL receive the delta and update its configuration within 10 seconds
3. THE Device_Simulator SHALL publish its reported state to the Device_Shadow whenever configuration changes occur
4. THE Tutorial_System SHALL include Lab_Module examples demonstrating Device_Shadow operations
5. THE Tutorial_System SHALL provide Architecture_Diagrams explaining Device_Shadow state synchronization
6. WHEN the Device_Simulator is offline, THE Device_Shadow SHALL retain the last reported state
7. WHEN the Device_Simulator reconnects after being offline, THE Device_Simulator SHALL synchronize with the Device_Shadow current desired state

### Requirement 13: Installation and Dependency Management

**User Story:** As a Beginner_User, I want easy installation of all dependencies, so that I can start learning quickly without environment issues.

#### Acceptance Criteria

1. THE Tutorial_System SHALL include a requirements.txt file listing all Python dependencies with pinned versions
2. THE Tutorial_System SHALL require Python 3.10 or higher as the minimum runtime version
3. THE Tutorial_System SHALL include installation instructions for aws-iot-device-sdk-python-v2 library
4. THE Tutorial_System SHALL include installation instructions for boto3 library for AWS service interaction
5. THE Tutorial_System SHALL include installation instructions for web framework dependencies for the Dashboard
6. WHEN dependencies are installed using the requirements.txt file, THE Tutorial_System SHALL be executable without additional package installations
7. THE Tutorial_System SHALL document any system-level prerequisites such as OpenSSL or Git

### Requirement 14: Multi-Device Simulation

**User Story:** As a Beginner_User, I want to simulate multiple devices simultaneously, so that I can learn about managing device fleets.

#### Acceptance Criteria

1. THE Tutorial_System SHALL support running multiple Device_Simulator instances concurrently with different configurations
2. WHEN multiple Device_Simulator instances are running, THE Dashboard SHALL display Telemetry_Data from all devices separately
3. THE Tutorial_System SHALL include Lab_Module examples demonstrating multi-device scenarios
4. WHEN a Device_Simulator instance is configured with a unique Thing identifier, THE Device_Simulator SHALL publish to Topics including the Thing identifier
5. THE Dashboard SHALL allow filtering and selecting specific devices for command transmission
6. THE Tutorial_System SHALL include scripts to launch multiple Device_Simulator instances with different configurations
7. THE Tutorial_System SHALL document resource considerations for running multiple simultaneous simulations

### Requirement 15: Educational Architecture Documentation

**User Story:** As a Beginner_User, I want visual architecture diagrams, so that I can understand how all components connect together.

#### Acceptance Criteria

1. THE Tutorial_System SHALL include an Architecture_Diagram showing the overall system architecture including Device_Simulator, AWS_IoT_Core, IoT_Rules, DynamoDB, and Dashboard
2. THE Tutorial_System SHALL include an Architecture_Diagram showing MQTT Topic structure and message flow
3. THE Tutorial_System SHALL include an Architecture_Diagram showing the security architecture including Certificate authentication flow
4. THE Tutorial_System SHALL include an Architecture_Diagram showing Device_Shadow state synchronization
5. THE Tutorial_System SHALL include an Architecture_Diagram showing data processing pipeline from device to storage
6. THE Architecture_Diagrams SHALL use standard notation for IoT components and AWS services
7. THE Architecture_Diagrams SHALL include labels and legends explaining all symbols and connections

### Requirement 16: Progressive Learning Path Enforcement

**User Story:** As a Beginner_User, I want the tutorial to guide me from simple to complex topics, so that I don't get overwhelmed with advanced concepts too early.

#### Acceptance Criteria

1. THE Learning_Path SHALL begin with IoT fundamentals before introducing AWS-specific concepts
2. THE Learning_Path SHALL introduce basic MQTT communication before advanced features like Device_Shadow
3. THE Learning_Path SHALL introduce single-device scenarios before multi-device fleet management
4. THE Learning_Path SHALL introduce data visualization before data processing and storage
5. THE Lab_Module sequence SHALL follow the Learning_Path with increasing complexity
6. THE Tutorial_System SHALL include prerequisite information at the beginning of each Lab_Module
7. THE Tutorial_System SHALL provide a learning roadmap showing the recommended order of topics and labs

### Requirement 17: Local Development Environment Support

**User Story:** As a Beginner_User, I want to run everything on my local machine, so that I can learn without requiring cloud infrastructure beyond AWS IoT Core.

#### Acceptance Criteria

1. THE Device_Simulator SHALL execute on Windows, macOS, and Linux operating systems
2. THE Dashboard SHALL be accessible through localhost without requiring external hosting
3. THE Tutorial_System SHALL include instructions for setting up the local development environment on each supported operating system
4. WHEN the Dashboard backend is started, THE Dashboard SHALL listen on a configurable local port with default 8000
5. THE Tutorial_System SHALL use local file storage for logs and temporary data
6. THE Tutorial_System SHALL not require Docker or containerization for basic operation
7. WHERE Docker is available, THE Tutorial_System SHALL include optional Dockerfiles for containerized execution

### Requirement 18: Data Format Standards

**User Story:** As a Beginner_User, I want consistent data formats throughout the tutorial, so that I can easily understand and work with the data.

#### Acceptance Criteria

1. THE Device_Simulator SHALL publish Telemetry_Data in JSON format with fields for timestamp, deviceId, temperature, humidity, and pressure
2. THE Command messages SHALL use JSON format with fields for commandType, parameters, and requestId
3. THE Telemetry_Data timestamp SHALL use ISO 8601 format with UTC timezone
4. THE Configuration_File SHALL support JSON format for device configuration parameters
5. THE Device_Shadow documents SHALL follow AWS IoT Device Shadow JSON specification
6. THE Tutorial_System SHALL include JSON schema definitions for all message types
7. THE Tutorial_System SHALL include examples of valid JSON messages for each message type

### Requirement 19: Testing and Validation Support

**User Story:** As a Beginner_User, I want to verify my setup is working correctly, so that I can confirm I completed each lab successfully.

#### Acceptance Criteria

1. THE Tutorial_System SHALL include validation scripts to test AWS connectivity before starting labs
2. THE Tutorial_System SHALL include validation scripts to verify Certificate configuration
3. THE Tutorial_System SHALL include validation scripts to confirm MQTT message publishing and receiving
4. WHEN a Lab_Module is completed, THE Tutorial_System SHALL provide expected output examples for comparison
5. THE Tutorial_System SHALL include unit tests for Device_Simulator core functionality
6. THE Tutorial_System SHALL include integration test examples demonstrating end-to-end data flow
7. THE Lab_Module SHALL include checkpoints with verification steps to confirm correct progress

### Requirement 20: Extensibility and Customization

**User Story:** As a Beginner_User, I want to customize and extend the tutorial examples, so that I can experiment beyond the basic exercises.

#### Acceptance Criteria

1. THE Device_Simulator SHALL support plugin architecture for adding new sensor types through configuration
2. THE Tutorial_System SHALL include examples of extending the Device_Simulator with custom sensors
3. THE Tutorial_System SHALL include examples of creating custom IoT_Rules for different use cases
4. THE Dashboard SHALL support adding new visualization widgets through modular design
5. THE Tutorial_System SHALL document extension points and APIs for customization
6. THE Tutorial_System SHALL include a Lab_Module focused on extending and customizing the base components
7. THE Tutorial_System SHALL provide templates for creating new Lab_Modules following the established pattern
