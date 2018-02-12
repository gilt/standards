# Databases

## Adopt

  - [Aster](http://www.asterdata.com)
    - for data warehouse
  - [DynamoDB](http://aws.amazon.com/dynamodb/)
  - [ElastiCache](http://aws.amazon.com/elasticache/) (preference to [Redis](http://redis.io/))
    - As a caching layer, **Adopt**.
    - As a primary data store, **Hold**.
  - [Postgresql](http://www.postgresql.org/) (preference to [RDS](https://aws.amazon.com/rds/))
    - Schema management for postgresql: [Schema evolution manager](https://github.com/gilt/schema-evolution-manager)
    - See [Deployment.md](Deployment.md) for more commentary on deployment options
  - [SOLR/Lucene](http://lucene.apache.org/solr/)
    - For indexed search, this is our most comfortable platform.
    
## Trial
  - [Elasticsearch](https://www.elastic.co/products/elasticsearch)
    
    - Potential replacement for SOLR.
    - The built-in Zookeeper-like component (Zen) is designed to work in the cloud (this could solve SolrCloud random inconsistent 
    state issues we experience).
    - Support for automatic shard rebalancing useful for horizontal scaling.

## Hold

  - [MongoDB](https://www.mongodb.org/)
  - [Voldemort](http://www.project-voldemort.com/voldemort/)

    Since our move to AWS we prefer to explore AWS-hosted solutions first to minimize maintenance overhead.
    For well structured data please consider RDS Postgresql.
    For KV document lookups please consider DynamoDB.
    For caching layer please consider ElastiCache Redis.
