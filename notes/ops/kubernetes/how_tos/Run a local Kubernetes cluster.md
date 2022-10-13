1. Open **Docker Desktop**
2. Go to **Settings**
3. Go to the **Kubernetes** tab
4. Check the **Enable Kubernetes** check box
5. Click the **Restart** button

Once Docker Desktop restarts you should have a Kubernetes cluster running on your machine. Easiest way to check this is to use [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl).

```shell
kubectl config get-contexts
```

If the installation has worked, you should see one called **docker-desktop**.