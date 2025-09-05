# 🚀 Kubernetes Tools & Scripts

This repository contains **useful tools and scripts for Kubernetes** to automate common DevOps and cluster administration tasks.  

It will grow with:
- Pod management scripts  
- Deployment and scaling automation  
- Health checks and troubleshooting tools  

---

## 📂 Repository Structure  

.
├── scripts/
│ ├── restart_pod.ksh # Script to delete and recreate a Kubernetes Pod
│ └── (future scripts here)
└── README.md

---

## 🛠️ Available Scripts  

| Script Name        | Description                                     | Language | Status        |
|--------------------|-------------------------------------------------|----------|---------------|
| `restart_pod.ksh`  | Deletes a pod and reapplies its YAML manifest    | ksh      | ✅ Ready       |

---

## ⚙️ Usage  

1. Clone this repository or copy the script to your machine  
2. Make the script executable:  
   ```bash
   chmod +x scripts/restart_pod.ksh
Run the script with:
./scripts/restart_pod.ksh <POD_NAME> <YAML_FILE_PATH> <NAMESPACE>
Example:
./scripts/restart_pod.ksh selenium-pod /home/user/selenium.yaml default
📜 Script Details
#!/bin/ksh
# Usage: ./restart_pod.ksh <POD_NAME> <YAML_FILE> <NAMESPACE>

# General variables
POD_NAME="$1"        # Pod name to restart
YAML_FILE="$2"       # Path to the YAML file for the pod
NAMESPACE="$3"       # Kubernetes namespace where the pod is located
LOG="/var/log/k8s-pod-check.log"  # Log file path

# Function to delete the pod
delete_pod() {
    echo "Deleting pod ${POD_NAME} in namespace ${NAMESPACE}..." >> ${LOG}
    kubectl delete pod ${POD_NAME} -n ${NAMESPACE} >> ${LOG}
    if [ $? -ne 0 ]; then
        echo "Error deleting the pod" >> ${LOG}
        exit 1
    fi
}

# Function to apply the YAML file
apply_yaml() {
    echo "Applying YAML ${YAML_FILE}..." >> ${LOG}
    kubectl apply -f ${YAML_FILE} -n ${NAMESPACE} >> ${LOG}
    if [ $? -ne 0 ]; then
        echo "Error applying the YAML file" >> ${LOG}
        exit 1
    fi
}

# Script start
date >> ${LOG}
# Check if the pod is running with all containers ready (e.g., 3/3)
kubectl get pod ${POD_NAME} -n ${NAMESPACE} | grep -w "${POD_NAME}" | grep "3/3" >> ${LOG}

if [ $? -eq 0 ]; then
    echo "Pod ${POD_NAME}: OK" >> ${LOG}
else
    # Save pod details and logs for troubleshooting
    kubectl describe pod ${POD_NAME} -n ${NAMESPACE} >> ${LOG}
    kubectl logs ${POD_NAME} -n ${NAMESPACE} >> ${LOG}
    
    # Delete and recreate the pod
    delete_pod
    echo "Waiting 10 seconds before recreating the pod..." >> ${LOG}
    sleep 10
    apply_yaml
    echo "Pod ${POD_NAME} recreated successfully." >> ${LOG}
fi

✅ Requirements
Kubernetes cluster access
kubectl installed and configured
A valid YAML manifest for the pod
📜 License
This project is licensed under the MIT License.
