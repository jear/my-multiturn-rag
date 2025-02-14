# my-multiturn-rag

NVidia sample (https://github.com/NVIDIA/GenerativeAIExamples/blob/main/RAG/examples/advanced_rag/multi_turn_rag/README.md)

Evaluating with labelStudio (https://labelstud.io/blog/evaluating-multi-turn-llm-chat-conversations-using-label-studio/)

```
# On the first GPU cluster, deploy accelerated Milvus
helm repo add zilliztech https://zilliztech.github.io/milvus-helm
helm repo update
k create ns milvus
helm install -n milvus milvus  zilliztech/milvus -f custom-values.yaml --set cluster.enabled=false --set etcd.replicaCount=1 --set minio.mode=standalone --set pulsar.enabled=false 
kubectl patch svc milvus -n milvus -p '{"spec": {"type": "LoadBalancer"}}'

# Change to another GPU cluster 
helm fetch https://helm.ngc.nvidia.com/nvidia/aiworkflows/charts/rag-app-multiturn-chatbot-24.08.tgz --username='$oauthtoken' --password=<YOUR API KEY>
helm show values rag-app-multiturn-chatbot-24.08.tgz > values.yaml

```
