# Setting Up Auxiliary Pipeline Systems

### Configuring the 'Config' Directory:

The 'config' directory plays a role in managing secrets and external services used by the pipeline. After making necessary updates to the required objects, you can apply them using the 'oc' command. 

Use this directory should you want to maintain Kubernetes `Secrets` rather an running the `oc` command. But, don't commit this directory to your Git repositories because it contains secret data.

To apply the configuration, run:

```bash
oc apply -f config/
```

## Advanced cluster security

### Creating Secrets for ACS Pipeline Tasks:

For ACS pipeline tasks, secrets are needed to handle the API token and ACS endpoint name.

To create a secret for the API token:

```bash
oc create secret generic stackrox-secret --from-literal=rox_api_token=<your-token-here>
```

The resulting secret should resemble:

```yaml
TODO: example secret definition
```

If your ACS instance is on the same cluster, use the exact command. Otherwise, update the address for your ACS instance:

```bash
oc create secret generic stackrox-endpoint --from-literal=rox_central_endpoint=central.stackrox.svc.cluster.local:443
```

The resulting secret should resemble:

```yaml
TODO: example secret definition
```

## GPG signing

### Preparing for GPG Verification:

The 'verify-source' task demonstrates GPG verification, the first step to authorise code changes in the build process. For a demonstration, you can set up GPG signing on MacOS by following [these instructions](../Docs/README.md). This method is not recommanded in a production context. After exporting your public key, store it as a secret:

```bash
oc create secret generic gpg-public-key --from-file=gpg-public-key.asc
```

The resulting secret should resemble:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: gpg-public-key
  namespace: security-qe-golden-path
data:
  gpg-public-key.asc: <your-base64-encoded-public-key>
type: Opaque
```

## Image Registry

The 'buildah' task will push the image to an image registry. Quay.io is the simple choice for this. Once your registry is set up, create a robot account with push access. Quay will provide a compatible `Secret` object; which can be applied to the cluster using `oc apply`. Ensure you include the namespace field as shown below:

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: image-registry-secret
  namespace: security-qe-golden-path
data:
  .dockerconfigjson: <encoded json object>
type: kubernetes.io/dockerconfigjson
```