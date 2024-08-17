# Allora-node-run-upgrade

# Remove all the files
```console
cd $HOME && cd basic-coin-prediction-node

sudo docker compose down -v

sudo docker stop $(docker ps -aq) 2>/dev/null

sudo docker rm $(docker ps -aq) 2>/dev/null

sudo docker rmi -f $(docker images -aq) 2>/dev/null

cd $HOME

sudo rm -rf basic-coin-prediction-node

```

# Redownload the allora files

```console

git clone https://github.com/allora-network/basic-coin-prediction-node

cd basic-coin-prediction-node

nano config.json
```
# Edit and enter your wallet seed phrase jn below code:

```console


{
    "wallet": {
        "addressKeyName": "testkey",
        "addressRestoreMnemonic": "Seed Phrase",
        "alloraHomeDir": "",
        "gas": "1000000",
        "gasAdjustment": 1.0,
        "nodeRpc": "https://sentries-rpc.testnet-1.testnet.allora.network/",
        "maxRetries": 1,
        "delay": 1,
        "submitTx": false
    },
    "worker": [
        {
            "topicId": 1,
            "inferenceEntrypointName": "api-worker-reputer",
            "loopSeconds": 5,
            "parameters": {
                "InferenceEndpoint": "http://inference:8000/inference/{Token}",
                "Token": "ETH"
            }
        },
        {
            "topicId": 2,
            "inferenceEntrypointName": "api-worker-reputer",
            "loopSeconds": 5,
            "parameters": {
                "InferenceEndpoint": "http://inference:8000/inference/{Token}",
                "Token": "ETH"
            }
        },
        {
            "topicId": 7,
            "inferenceEntrypointName": "api-worker-reputer",
            "loopSeconds": 5,
            "parameters": {
                "InferenceEndpoint": "http://inference:8000/inference/{Token}",
                "Token": "ETH"
            }
        }
    ]
}

```

click Ctrl + X Then Y

```console

chmod +x init.config
./init.config

docker compose up --build
```
open new window 


```console
cd basic-coin-prediction-node

docker compose ps
```

# for logs of the worker

```console

docker compose logs -f worker
```
click ctrl+c tl exit the logs



# To run the nide after turning of pc

```console
cd basic-coin-prediction-node

sudo docker compose up -d

docker ps
```
