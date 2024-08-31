# Chapter 4 - Encoding

Data is encoded/decoded to be transferred between different systems (either internally or externally).

The problem encoding solves are changing in reading/writing systems to allow *rolling upgrade*. System evolves and making that upgrade to be gradual will reduce downtime & cost of releases.

This causes a problem with backward/forward compatibility due to different versions of systems trying to read/write data:

- Backward compatibility: V2 code reads V1 data (CodeV2 → DataV1)
- Forward compatibility: V1 code reads V2 data (CodeV1 → DataV2)

# **Decoding/encoding method:**

- Language-specific format: Eg: Python Pickle, Ruby Marshall
    - Good for simplicity
    - Bad bc outside of existing system, language, it wouldn't be decode-able

- Human-readable: XML, JSON, CSV.
    - Good for readability, systems compatibility
    - Bad bc of size (text is not efficient), not good for supporting forward/backward compatibility.

- **Binary**
    - Binary file is preferred due to the significant saving in memory → less transportation cost
    - Pure-binary:
        - Cost is low
        - But does not support backward/forward compatibility:
            - CodeV1 receiving DataV2 won’t be able to decode completely (eg: adding new keys in DataV2 will be missed by CodeV1 code)
            - CodeV2 receiving DataV1 data also won’t be able to decode completely (eg: removing keys from CodeV2 will make DataV1 data corrupt)
        - Also does not support changing in attribute name

```json
# Data example

username/string/cuongtn/color/string/red/array/string/snowboarding/running/EOF
```

### Protocol Buffer/Thrift:

Method: having a model defining attributes, data type, and a tag (id-like)

```json
# Model (could be human-readable)

{
    user: string, 01
    favourit_color: string, 02
    interests: array<string> 03
}

# Data (translated binary)

01/string/cuongtn/02/string/red/03/array/string/snowboarding/running/EOF
```

How does Protocol Buffer/ Thift do backward/forward compatibility

- Backward compatibility
    - CodeV2 receiving DataV1: able to decode bc of the tag (
        - eg: CodeV2 adding new field aka new tag will be able to decode DataV1 bc that tag doesn’t exist in DataV1
        - eg: CodeV2 removing field aka tag will just skip the same tag in DataV1 → decodable
- Forward compatibility
    - CodeV1 receiving DataV2: able to decode also bc of tag
        - eg: DataV2 having new tag, CodeV1 doesn’t map that tag and just skip it
        - DataV2 removing the same tag, CodeV1 also skip that tag
- Tag name (attribute) updating is also feasible bc: model file is updated, data file doesn’t need to be updated
- Only Tag ID can’t never be updated, similar to primary key which is fine
- Adding new field, can’t make it required, or will need default value

### Avro

- good for dynamically generated schemas

Q: Schema vs non-Schema
A:
- Good for documentation

## Data communication

### Database

- Backward compatibility is required, data written in the past needs to be readable by future code
- Forward compatibility is required bc new application when getting deployed into multiple nodes might not be the same versions immediately, so old code might need toread new data
    - Missing field problem: solvable in the application layer, but developers have to be aware of it (known unknown)
- Data outlives code -> migration is required

### Between Client - Service/ Service - Service

- Web to Server: HTTP Client
- Mobile to Server: HTTP Client
- Service to Service: SOA/Microservices

Web services can be between:
- Client to Server
- Server to Server:
    - Within the organization
    - With different organization (eg: oauth)

2 type of communication

- REST: design philosophy based on HTTP, using JSON, doesn't allow a lot of
- SOAP: does not follow HTTP, XML-based language called Web Services Description Language (WSDL), allow for code generation based on schema, complicated to use, not human-readable, relied heavily on tooling, IDE to make it work

What about RPC? Trying to use RPC as the interface for network requests are problematic:

- Functions call has 3 out come: return, not return, exception. Network has the 4th outcome: timeout
- Functions might be called multiple times, network calls are shouldn't be unless there's idempotency protocol implemented (eg: multiple POST request is no bueno)
- Functions call don't have to deal with network problems
- Functions call are deterministic in time, network calls are not
- Different services might use different programming languages, RPC need to encode things properly to be able to decode by different langauges

Regardless RPC is still being used/implemented:

- making clear that a function call is async (using Future/Promises)
- Using binary encoding provides better performance than non binary ones in REST + SOAP
- gRPC supports *stream*

A possible conclusion here is that if performance does not matter too much, using network calls are easier/ more straight forward, to a point where you want to significantly save on network-related cost, then RPC can be considered.

REST is being used in most public APIs.
RPC is being used within organizational services + most likely same data center

`gRPC` is RPC using ProtocolBuffers

### Message Broker

```
Service (Publisher) -> MessageQueue -> ServiceA (Subscriber)
                                    -> ServiceB (subscriber)
```

MessageBroker is advantageous to web services:

- Request only, no response
- Sender doesn't need to know about receiver (& vice versa) -> Sender/Receiver can be replaced independently, which happens a lot in a VM environments without fixed IPs
-

Eg: RabbitMQ, ActiveMQ, Kafka

#### Distributed actor framework

`Actor Model` is a programming model for concurrency in a single process

Each actor represent a client, or a service.

Still some unknown here

Q: What are the example of Actor Model? Erlang OTP


Eg: Erlang OTP


# Further learning & references

- Erlang OTP
