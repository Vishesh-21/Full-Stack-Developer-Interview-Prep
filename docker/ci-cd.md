**CI/CD Pipelines**

CI/CD stands for Continuous Integration and Continuous Deployment/Delivery. A pipeline is basically an automated workflow that takes your code from commit → build → test → package → deploy. CI/CD is an automated process that helps teams deliver code faster and safely.

**_CI (Continuous Integration)_** : means every time a developer pushes code, the system automatically :

- Builds the application
- Runs tests
- Checks code quality
- Fails fast if something is broken

**_CD (Continuous Deployment/Delivery)_** means once CI passes:

- The application is automatically deployed to staging or production
- Or kept ready for manual approval (depending on setup)

---

**How CI/CD Pipelines Work**

let's take you are using github, docker, kubernetes and jenkins or github actions

1. Developer pushes code to main branch.
2. CI tool triggers automatically.
3. It installs dependencies.
4. Runs unit tests.
5. Builds a Docker image.
6. Pushes the image to a container registry.
7. CD step deploys that image to Kubernetes.
8. Health checks run.
9. If everything is healthy → deployment is successful.
   If anything fails → pipeline stops immediately.

---

**Why CI/CD Is Important**

- Faster releases
- Fewer production bugs
- Rollbacks become easy
- Better collaboration
- Confidence in deployments

**_Without CI/CD, teams manually build, test, deploy — which leads to mistakes and downtime._**

---

**What is the difference between Continuous Delivery and Continuous Deployment?**

- **_Continuous Delivery_** → Code is automatically built and tested, but deployment to production requires manual approval.

- **Continuous Deployment**→ Code is automatically deployed to production without human intervention after tests pass.

---

**What are the key stages in a CI/CD pipeline?**

- Source (Code commit trigger) ➡️ build ➡️ test ➡️ artifact creation(docker image, build packages) ➡️ deployment ➡️ monitoring/validation

---

**What happens if a deployment fails?**

- Automatic rollback to previous stable version
- Blue-Green or Canary deployment strategy
- Health checks and readiness probes

The idea is: users should not feel the failure.

---

**How would you improve a slow CI pipeline?**

- Use caching for dependencies
- Parallel test execution
- Use smaller Docker layers
- Run only affected tests (not full test suite every time)
- Use incremental builds

---

**What is a Blue-Green deployment?**
You maintain two environments:

- Blue → current production
- Green → new version

You deploy the new version to Green. If everything works fine, you switch traffic from Blue to Green.

Rollback is easy — just switch traffic back.

---

**What is Canary deployment?**
You release the new version to a small percentage of users first (like 5–10%). If there are no errors, you gradually increase traffic.

It reduces risk compared to full deployment.

---

**How do you make a CI/CD pipeline secure?**

- Use role-based access control.
- Store secrets in secret managers.
- Enable artifact signing.
- Use vulnerability scanning for Docker images.
- Restrict production deployment permissions.
- Enable branch protection rules.

---
