### Config and Wallet Accounts for Hyperledger Besu Multi-Node Setup

* [Hyperledger Besu Private Network using Docker](https://www.polarsparc.com/xhtml/BesuPrivateCliqueDocker.html)

### How to run

```
bash
export BESU_HOME=`pwd`

docker run --rm --name bank -d --network host -e BESU_OPTS="--add-opens java.base/jdk.internal.misc=ALL-UNNAMED -Dio.netty.tryReflectionSetAccessible=true" -u $(id -u $USER):$(id -g $USER) -v $BESU_HOME/data/bank:/opt/besu/data -v $BESU_HOME/data/bank:/opt/besu/keys -v $BESU_HOME/data/bank:/opt/besu/public-keys -v $BESU_HOME/conf/bank-config.toml:/config/config.toml -v $BESU_HOME/conf/genesis.json:/config/genesis.json hyperledger/besu:22.7.7 --config-file=/config/config.toml

docker run --rm --name buyer -d --network host -e BESU_OPTS="--add-opens java.base/jdk.internal.misc=ALL-UNNAMED -Dio.netty.tryReflectionSetAccessible=true" -u $(id -u $USER):$(id -g $USER) -v $BESU_HOME/data/buyer:/opt/besu/data -v $BESU_HOME/data/buyer:/opt/besu/keys -v $BESU_HOME/conf/buyer-config.toml:/config/config.toml -v $BESU_HOME/conf/genesis.json:/config/genesis.json hyperledger/besu:22.7.7 --config-file=/config/config.toml

docker run --rm --name dealer -d --network host -e BESU_OPTS="--add-opens java.base/jdk.internal.misc=ALL-UNNAMED -Dio.netty.tryReflectionSetAccessible=true" -u $(id -u $USER):$(id -g $USER) -v $BESU_HOME/data/dealer:/opt/besu/data -v $BESU_HOME/data/dealer:/opt/besu/keys -v $BESU_HOME/conf/dealer-config.toml:/config/config.toml -v $BESU_HOME/conf/genesis.json:/config/genesis.json hyperledger/besu:22.7.7 --config-file=/config/config.toml

docker run --rm --name dmv -d --network host -e BESU_OPTS="--add-opens java.base/jdk.internal.misc=ALL-UNNAMED -Dio.netty.tryReflectionSetAccessible=true" -u $(id -u $USER):$(id -g $USER) -v $BESU_HOME/data/dmv:/opt/besu/data -v $BESU_HOME/data/dmv:/opt/besu/keys -v $BESU_HOME/conf/dmv-config.toml:/config/config.toml -v $BESU_HOME/conf/genesis.json:/config/genesis.json hyperledger/besu:22.7.7 --config-file=/config/config.toml
```