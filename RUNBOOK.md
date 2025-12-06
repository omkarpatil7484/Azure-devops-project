🧠 High Memory Usage Runbook

This runbook explains what actions to take when a High Memory Alert is triggered in a Kubernetes cluster.

1️⃣ Check Node-Level Memory Usage

Run the following command to check how much memory each node is using:

kubectl top nodes


📌 If memory usage is above 80%, continue to the next step.

2️⃣ Identify Which Pod Is Using the Most Memory
kubectl top pod -A


📌 Example output:

NAMESPACE     NAME                                     CPU   MEMORY
default       devops-demo-app                          1m    42Mi
monitoring    grafana                                  6m    672Mi
monitoring    prometheus                               23m   244Mi


➡️ Identify the pod consuming the highest memory.

3️⃣ Inspect the Pod
kubectl describe pod <pod-name> -n <namespace>


Check for:

🚨 High restart count

❌ OOMKilled (Out Of Memory) errors

⚠️ Any warnings or error logs

4️⃣ Fix Actions
🔧 Option 1 — Restart the Pod
kubectl delete pod <pod-name> -n <namespace>


➡️ Kubernetes will automatically create a replacement pod.

🔧 Option 2 — Increase Memory Resource Limits

Modify Deployment YAML or Helm chart:

resources:
  limits:
    memory: "1Gi"
  requests:
    memory: "512Mi"


➡️ Apply the updated configuration:

kubectl apply -f deployment.yaml

🔧 Option 3 — Scale the Deployment

If the workload is high, increase replicas:

kubectl scale deploy <deploy-name> --replicas=2 -n <namespace>

5️⃣ If the issue continues:

Notify the team (DevOps Lead / SRE)

Scale the cluster (add new node pool or increase node size)

📣 Slack / Teams Update Template
🔔 Alert Triggered: High Memory Usage  
📌 Pod: <pod-name>  
🕒 Time: <timestamp>  
🔍 Action Taken: Restarted / Scaled / Updated limits  
📈 Next Review: After 10 minutes

✅ Resolution Checklist

✔ Memory usage returned to normal (<80%)
✔ Pod stable (no restarts/errors)
✔ No new alerts for 15–20 minutes
