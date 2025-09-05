# 🚀 Kubernetes Tools & Scripts Collection

Welcome to the **Kubernetes Tools & Scripts** repository! 🎯  
This repo is designed to centralize **useful scripts, automation tools, and utilities** for managing Kubernetes clusters efficiently.  

Whether you're dealing with **pods, deployments, namespaces**, or just want to automate repetitive tasks, this repository will grow into a **toolbox for Kubernetes admins and DevOps engineers**.  

---

## 📂 Repository Structure  

k8s-tools/
│
├── restart_pod.ksh # Script to delete and recreate a Pod automatically
├── scale_deployment.ksh # (Future) Script to scale deployments up/down
├── check_nodes.ksh # (Future) Node health check script
├── README.md # This file
└── ...

Each tool will come with:
- **Code commented in English** for clarity  
- **Usage instructions** with examples  
- **Logging support** where needed  

---

## ⚙️ Getting Started  

### Prerequisites  

- Access to a Kubernetes cluster  
- `kubectl` configured properly  
- Basic knowledge of shell scripting  

---

## 🛠️ Available Tools  

| Tool Name           | Description                                     | Language   | Status        |
|---------------------|------------------------------------------------|------------|---------------|
| `restart_pod.ksh`   | Deletes a pod and reapplies its YAML manifest    | ksh        | ✅ Ready       |
| `scale_deployment.ksh` | Scale Kubernetes deployments up or down         | ksh        | 🔄 Coming soon |
| `check_nodes.ksh`   | Check cluster nodes status and resource usage     | ksh        | 🔄 Coming soon |

---

## 📖 Usage Example  

To restart a pod using `restart_pod.ksh`:

```bash
./restart_pod.ksh <POD_NAME> <YAML_FILE_PATH> <NAMESPACE>
Example:
./restart_pod.ksh selenium-pod /home/user/selenium.yaml default
🚧 Roadmap
 Add scripts for Deployment scaling
 Add Node health-check tool
 Add namespace cleanup script
 Include Helm automation examples
 CI/CD with GitHub Actions
🤝 Contributing
Contributions are welcome!
Feel free to fork this repo, submit pull requests, or open issues for new ideas and bug reports.
📜 License
This repository is licensed under the MIT License.
⭐ Support
If you find this repository useful, consider starring it on GitHub to help others discover it!

---

Si quieres, puedo dejarte **el primer commit del repo** con este README.md y la carpeta inicial para scripts en un formato listo para subir.  

¿Quieres que te prepare la estructura inicial del repositorio con todo listo para GitHub?
