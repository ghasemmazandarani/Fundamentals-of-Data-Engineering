# Everything I Learned from the Second Chapter of the Book "Fundamentals of Data Engineering"

## Lifecycle Flexibility

The stages of the data engineering lifecycle may not follow a strict sequence; they can repeat, overlap, and intertwine in unexpected ways. This flexibility reflects the dynamic nature of data handling in complex systems.

## Understanding Source Systems

A source system is the origin of data within the data engineering lifecycle. Examples include:
- IoT devices
- Application message queues
- Transactional databases

While data engineers consume data from these systems, they typically do not control or own them. It’s crucial for data engineers to understand how these systems generate data, including any quirks or limitations, such as whether running analytical queries on a source system could lead to resource contention or performance issues.

## Schema in Data Systems

- **Schemaless Systems**: Schemaless does not mean "no schema"; instead, it means the schema is defined as data is written, such as in a message queue, flat file, or document database like MongoDB.
- **Fixed Schema Systems**: Traditional relational databases enforce a fixed schema, requiring application data to conform to it.

A critical task for data engineers is transforming raw data from the source system schema into valuable analytics-ready output.

## Choosing Storage Solutions

Selecting the right storage solution is foundational to a successful data lifecycle and one of its most complex stages. Storage is present at multiple stages, including source systems, ingestion, transformation, and serving, and influences how data is utilized throughout the lifecycle. For instance:
- **Cloud Data Warehouses**: Can handle storage, data processing, and serve data to analysts.
- **Streaming Frameworks (e.g., Apache Kafka, Pulsar)**: Function as ingestion, storage, and query systems for message data.
- **Object Storage**: Commonly used for data transmission layers.

## Data Access Frequency: Hot, Lukewarm, and Cold Data

The access frequency or "temperature" of data dictates storage choices:
- **Hot Data**: Frequently accessed, stored for fast retrieval (e.g., serving user requests).
- **Lukewarm Data**: Accessed occasionally, such as weekly or monthly.
- **Cold Data**: Rarely accessed, stored for compliance or backup purposes, often in archival systems.

## Data Ingestion Concepts

### Batch vs. Streaming Ingestion

- **Batch Ingestion**: Processes data in large chunks, suitable for use cases like model training or weekly reporting.
- **Streaming Ingestion**: Handles data as a continuous flow, useful for real-time applications but often more complex and costly.

### Push vs. Pull Ingestion

- **Push Model**: The source system pushes data to the target system (database, object store, filesystem).
- **Pull Model**: The ingestion system pulls data from the source system.

In practice, both models may be combined as data moves through a pipeline.

## ETL and CDC Processes

### ETL (Extract, Transform, Load)

The ETL process is commonly used in batch-oriented workflows. The "extract" stage typically follows a pull ingestion model, where data is queried from a source on a set schedule.

### Change Data Capture (CDC)

CDC enables continuous data synchronization by capturing data changes. There are multiple methods:
- **Message-based CDC**: Triggers a message with each database row change, which is then picked up by the ingestion system.
- **Binary Log-based CDC**: Uses database binary logs to record all commits; the ingestion system reads these logs without directly querying the database, reducing load.
- **Timestamp-based CDC**: In a batch pattern, pulls rows that changed since the last update by querying based on timestamps.

## Streaming Ingestion for Real-Time Data

In some cases, data bypasses a backend database and is sent directly to an endpoint via a streaming platform. This method is advantageous for scenarios like IoT sensor data, where each reading is treated as an event, enabling real-time processing. This pattern is also popular in software applications, as it simplifies processing and enhances the flexibility of downstream analytics.


## Data Transformation in the Data Engineering Lifecycle

### Overview
Data transformation is a critical phase where raw data is converted into meaningful information for downstream use. Without proper transformations, data remains inert and unusable for analytics, reporting, or machine learning.

### Key Components

#### Basic Transformations
* Converting data types (strings to numbers/dates)  
* Standardizing record formats
* Removing invalid records

#### Advanced Transformations
* Schema modifications
* Data normalization  
* Large-scale aggregation
* Feature engineering for ML

### Important Considerations
1. **ROI Analysis**
  * Cost evaluation
  * Business value assessment

2. **Technical Aspects**
  * Simplicity of transformation
  * Minimizing data movement
  * Integration with business rules

3. **Processing Methods**
  * Batch processing
  * Stream processing

### Business Impact
* Supports data modeling
* Implements business logic
* Enables financial reporting
* Facilitates machine learning

### Best Practices
* Keep transformations simple and isolated
* Align with business rules
* Minimize data movement
* Standardize business logic implementation
* Automate feature engineering processes

This stage marks where data begins to create tangible value for organizations through structured transformation processes.

