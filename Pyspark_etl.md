
### Pseudocode

```
def connectRdbms(spark, config):
    conf = ExtractConfig(config)
    df = spark.read.jdbc(url=conf.url,table='conf.table',properties=conf)
    return df
    
def serialize(df):
    df = connectRdbms(config)
    # TODO: Data to serialize
    #       and return the serialized code 
    return df_ser
    
def writeToHdfs(spark, config, df_ser):
    df.write.format(avro).save(pathToHdfs)


def main(Object):
    # spark will be injected from a seperate dependency py file
    spark, log, config = build_spark(
        app_name='pyspark_pipeline',
        files=['configs/conf.json'])
    df = connectRdbms(config)
    df_serialized_data = serialize(df)
    writeToHdfs(config, df_ser)
    

```
