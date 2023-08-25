# Secure Build Pipeline Demonstrator: Guiding You Along Golden Pathways to Secure Software Deployment

Welcome to the Secure Build Pipeline Demonstrator! 🚀 In the realm of software development, having a well-defined and secure route from code creation to production deployment is invaluable. This project acts as your guide along those "golden pathways" — structured processes that ensure your software is safe, dependable, and thoroughly traceable.

## The Power of Golden Pathways

Imagine software development as a journey where well-charted paths lead to success. Just as travelers follow established routes, your software needs a dependable path from its source code to its final deployment. This "golden pathway" guarantees that your applications are constructed securely and systematically, adhering to best practices at every step.

## Navigating the Secure Build Pipeline

At the core of this initiative is the Secure Build Pipeline Demonstrator—a practical example that showcases how to establish your own dependable deployment process. Here's what it offers:

1. **Commit Verification:** The journey starts with validating Git commits. Only code that passes rigorous GPG verification gains access to the secure deployment process.

2. **Dockerfile-Based Builds:** If you're familiar with Dockerfiles, you're in luck. Our demonstrator seamlessly integrates Dockerfile-based builds into the process.

3. **Vulnerability Assessment:** Prioritising software security is paramount. We use Red Hat's Advanced Cluster Security scanner to identify vulnerabilities and furnish actionable reports.

4. **Utilising Syft:** Employ Syft to generate a comprehensive inventory of your software's components—a transparent look at what constitutes your application.

5. **Ensuring Transparency:** Ever wondered about an image's origins? Our build process captures essential details like commit authorship and dates, offering a clear journey from initial code to the final image.

## Getting Started

To kick off your journey with the Secure Build Pipeline Demonstrator, follow these steps:

1. **Install Operators:**

   Start by installing the operators that drive the Secure Build Pipeline. Run the following command:

```
oc apply -f openshift-subscriptions.yaml
```

2. **Install Supporting Components (Optional):**

   If you're testing this on a single cluster, consider installing the supporting components. Execute this command:

```
oc apply -f auxiliary-pipeline-systems.yaml
```

3. **Setup Required Services:**
   
   You'll need to set up specific services as per the directions provided in the [Config/README.md](Config/README.md) guide.

4. **Apply the Pipeline:**
   
   Lastly, apply the secure pipeline to your cluster. Use the following command:

```
oc apply -f secure-pipeline.yaml
```
