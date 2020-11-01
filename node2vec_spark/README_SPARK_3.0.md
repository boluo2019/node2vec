
## 在spark 3.0.1 & hadoop 3.2.0 上跑node2vec

### 下载spark
- https://spark.apache.org/downloads.html

### 修改依赖
由于原作者是在spark 1.6.1 & hadoop 2.7.1上写的代码，所以我们要改一下[pom.xml](pom.xml)

### 执行embedding
- cd spark目录
- bin/spark-submit --class com.navercorp.Main ~/work/0-source/github/boluo-node2vec/node2vec/node2vec_spark/target/node2vec-0.0.2-SNAPSHOT.jar --cmd randomwalk --p 100.0 --q 100.0 --walkLength 40 --input ~/work/0-source/github/boluo-node2vec/node2vec/graph/karate.edgelist --output /tmp/hqx-out/randomwalk-out

### 执行embedding
- cd spark目录
- bin/spark-submit --class com.navercorp.Main ~/work/0-source/github/boluo-node2vec/node2vec/node2vec_spark/target/node2vec-0.0.2-SNAPSHOT.jar --cmd embedding --input /tmp/hqx-out/randomwalk-out/part-00000 --nodePath ~/work/0-source/github/boluo-node2vec/node2vec/graph/v.list --output /tmp/hqx-out/hqx-embedding-out

### 执行node2vec
- cd spark目录
- bin/spark-submit --class com.navercorp.Main ~/work/0-source/github/boluo-node2vec/node2vec/node2vec_spark/target/node2vec-0.0.2-SNAPSHOT.jar --cmd node2vec --input ~/work/0-source/github/boluo-node2vec/node2vec/graph/karate.edgelist --output /tmp/hqx-out/hqx-node2vec-out


### 其他数据集
