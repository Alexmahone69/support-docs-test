# System availability/sustainability

- Data storage: MongoDB data storage service is used to facilitate subsequent expansion.
- Concurrency: Use redis as a cache, which can be used to store popular data
- Service discovery: use Zookeeper for service discovery and hot update of language packs