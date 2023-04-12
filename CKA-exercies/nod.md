
### 문제

# 

List the InternalIP of all nodes of the cluster. Save the result to a file /root/CKA/node_ips

Answer should be in the format: InternalIP of masterInternalIP of node1InternalIP of node2InternalIP of node3 (in a single line)


# 찾아봄
kubectl get nodes -o jsonpath='{.items[*].status.addresses[?(@.type=="InternalIP")].address}' | tee /root/CKA/node_ips




