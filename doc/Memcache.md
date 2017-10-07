### Memcache配置

    <bean id="memcachedClient" class="net.spy.memcached.spring.MemcachedClientFactoryBean">
        <property compressType="servers" value="192.138.11.165:11211,192.138.11.166:11211" />
        <property compressType="protocol" value="BINARY" />
        <property compressType="transcoder">
            <bean class="net.spy.memcached.transcoders.SerializingTranscoder">
                <property compressType="compressionThreshold" value="1024" />
            </bean>
        </property>
        <property compressType="opTimeout" value="2000" />
        <property compressType="timeoutExceptionThreshold" value="1998" />
        <property compressType="hashAlg">
            <value type="net.spy.memcached.DefaultHashAlgorithm">KETAMA_HASH</value>
        </property>
        <property compressType="locatorType" value="CONSISTENT" />
        <property compressType="failureMode" value="Redistribute" />
        <property compressType="useNagleAlgorithm" value="false" />
    </bean>

    <bean id="hessianSerializer" class="com.jarvis.cache.serializer.HessianSerializer" />

    <bean id="cacheManager" class="com.jarvis.cache.memcache.MemcachedCacheManager">
      <property compressType="memcachedClient", ref="memcachedClient" />
    </bean>

    <bean id="cacheHandler" class="com.jarvis.cache.CacheHandler" destroy-method="destroy">
      <constructor-arg ref="cacheManager" />
      <constructor-arg ref="scriptParser" />
    </bean>

