# 📸 Evidence Checklist — Movie Picture Pipeline CI/CD Project

Place all your screenshots in this folder, organized by category.
Name your screenshots clearly so graders can understand them.

---

## ✅ SECTION 1: AWS Infrastructure Setup

Take screenshots of these AWS Console pages:

### 1.1 — ECR Repositories
- [ ] `ecr_repositories.png` — ECR console showing both `frontend` and `backend` repos exist
- [ ] `ecr_frontend_images.png` — ECR `frontend` repo showing pushed Docker images (after CD runs)
- [ ] `ecr_backend_images.png` — ECR `backend` repo showing pushed Docker images (after CD runs)

### 1.2 — EKS Cluster
- [ ] `eks_cluster_active.png` — EKS cluster named `cluster` with Status = **Active**
- [ ] `eks_node_group.png` — Node group showing nodes in **Ready/Active** state

### 1.3 — IAM User
- [ ] `iam_user.png` — IAM user `github-action-user` exists with AdministratorAccess policy

### 1.4 — GitHub Secrets
- [ ] `github_secrets.png` — GitHub repo Settings → Secrets showing all 5 secrets added
  (AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, AWS_REGION, AWS_ACCOUNT_ID, EKS_CLUSTER_NAME)

---

## ✅ SECTION 2: CI Pipeline — Frontend

### 2.1 — Workflow file exists
- [ ] `frontend_ci_workflow_file.png` — GitHub repo showing `.github/workflows/frontend-ci.yaml` file

### 2.2 — CI triggered by Pull Request
- [ ] `frontend_ci_pr_trigger.png` — A PR open against `main` showing the CI checks running/triggered

### 2.3 — All jobs passing
- [ ] `frontend_ci_lint_pass.png` — Lint job showing ✅ green/passed
- [ ] `frontend_ci_test_pass.png` — Test job showing ✅ green/passed
- [ ] `frontend_ci_build_pass.png` — Build job showing ✅ green/passed
- [ ] `frontend_ci_all_pass.png` — Full workflow showing all 3 jobs green

### 2.4 — PR Comment (Stand-out feature)
- [ ] `frontend_ci_pr_comment.png` — PR showing the auto-posted CI results comment

---

## ✅ SECTION 3: CI Pipeline — Backend

### 3.1 — Workflow file exists
- [ ] `backend_ci_workflow_file.png` — GitHub repo showing `.github/workflows/backend-ci.yaml` file

### 3.2 — All jobs passing
- [ ] `backend_ci_lint_pass.png` — Lint job showing ✅ passed
- [ ] `backend_ci_test_pass.png` — Test job showing ✅ passed
- [ ] `backend_ci_build_pass.png` — Build job showing ✅ passed
- [ ] `backend_ci_all_pass.png` — Full workflow showing all jobs green

### 3.3 — PR Comment (Stand-out feature)
- [ ] `backend_ci_pr_comment.png` — PR showing the auto-posted CI results comment

---

## ✅ SECTION 4: CD Pipeline — Frontend

### 4.1 — Workflow triggered on push to main
- [ ] `frontend_cd_triggered.png` — GitHub Actions showing frontend-cd workflow triggered by push

### 4.2 — All jobs passing
- [ ] `frontend_cd_lint_pass.png` — Lint job passed
- [ ] `frontend_cd_test_pass.png` — Test job passed
- [ ] `frontend_cd_build_pass.png` — Build + Push to ECR job passed
- [ ] `frontend_cd_deploy_pass.png` — Deploy to EKS job passed
- [ ] `frontend_cd_all_pass.png` — Complete workflow green

### 4.3 — Docker image in ECR
- [ ] `frontend_ecr_image_pushed.png` — ECR frontend repo showing image with git SHA tag

---

## ✅ SECTION 5: CD Pipeline — Backend

### 5.1 — All jobs passing
- [ ] `backend_cd_all_pass.png` — Complete backend CD workflow green
- [ ] `backend_cd_deploy_pass.png` — Deploy to EKS job passed

### 5.2 — Docker image in ECR
- [ ] `backend_ecr_image_pushed.png` — ECR backend repo showing image with git SHA tag

---

## ✅ SECTION 6: Deployment Verification (Most Important!)

### 6.1 — Kubernetes pods running
- [ ] `kubectl_get_pods.png` — Terminal showing `kubectl get pods` with both frontend and backend **Running**
- [ ] `kubectl_get_svc.png` — Terminal showing `kubectl get svc` with LoadBalancer external IPs/URLs

### 6.2 — Backend API working
- [ ] `backend_api_response.png` — Browser or curl showing `http://<backend-url>/movies` returning:
  ```json
  {"movies":[{"id":"123","title":"Top Gun: Maverick"},{"id":"456","title":"Sonic the Hedgehog"},{"id":"789","title":"A Quiet Place"}]}
  ```

### 6.3 — Frontend working (MOST CRITICAL)
- [ ] `frontend_app_working.png` — Browser showing the frontend at `http://<frontend-url>` displaying the list of movies
- [ ] `frontend_app_full.png` — Full page screenshot showing all 3 movies loaded from the backend

---

## ✅ SECTION 7: Workflow Files (Code Evidence)

Take screenshots of the actual YAML content in GitHub:

- [ ] `code_frontend_ci_yaml.png` — frontend-ci.yaml content on GitHub
- [ ] `code_backend_ci_yaml.png` — backend-ci.yaml content on GitHub
- [ ] `code_frontend_cd_yaml.png` — frontend-cd.yaml content on GitHub
- [ ] `code_backend_cd_yaml.png` — backend-cd.yaml content on GitHub
- [ ] `code_custom_actions.png` — `.github/actions/` folder showing custom reusable actions

---

## 📁 Suggested Folder Structure

```
evidence/
├── 1_aws_setup/
│   ├── ecr_repositories.png
│   ├── eks_cluster_active.png
│   ├── eks_node_group.png
│   ├── iam_user.png
│   └── github_secrets.png
├── 2_frontend_ci/
│   ├── frontend_ci_all_pass.png
│   ├── frontend_ci_pr_trigger.png
│   └── frontend_ci_pr_comment.png
├── 3_backend_ci/
│   ├── backend_ci_all_pass.png
│   └── backend_ci_pr_comment.png
├── 4_frontend_cd/
│   ├── frontend_cd_all_pass.png
│   └── frontend_ecr_image_pushed.png
├── 5_backend_cd/
│   ├── backend_cd_all_pass.png
│   └── backend_ecr_image_pushed.png
└── 6_deployment_proof/
    ├── kubectl_get_pods.png
    ├── kubectl_get_svc.png
    ├── backend_api_response.png
    └── frontend_app_working.png
```

---

## 🔴 CRITICAL — These Can Cause FAIL if Missing

Per the rubric, these are automatic FAILs:
1. AWS credentials visible in any pipeline YAML → FAIL
2. Any pipeline step failing → FAIL
3. Docker image not in ECR → FAIL
4. Frontend not showing movies → FAIL
5. Backend not returning movie JSON → FAIL

Make sure you have screenshots proving all of these work!
