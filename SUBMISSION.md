# DevOps Capstone - Assignment Answers

**Public repository:** https://github.com/yaqyn/devops-capstone-project

All screenshots and output files are in the `deliverables/` folder of this repository.

---

## Task 1
**Answer (README.md URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/README.md

The README shows the project name **devops-capstone-project**, the capstone description, and the **CI Build passing** status badge.

---

## Task 2
**Answer (user-story.md URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/.github/ISSUE_TEMPLATE/user-story.md

---

## Task 3
**Answer:** Upload `deliverables/planning-userstories-done.png` - shows all seven user stories in the **New issues** column.

---

## Task 4
**Answer:** Upload `deliverables/planning-productbacklog-done.png` - shows the **Icebox** column with "Containerize your microservice using Docker" and "Deploy your Docker image to Kubernetes".

---

## Task 5
**Answer:** Upload `deliverables/planning-labels-done.png` - shows the **Product backlog** stories labelled **technical debt** and **enhancement**.

---

## Task 6
**Answer:** Upload `deliverables/planning-kanban-done.png` - shows the **Sprint backlog** stories with estimates (3, 5, 3, 3, 5) assigned to **Sprint 1**.

---

## Task 7
**Answer (setup.cfg URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/setup.cfg

---

## Task 8
**Answer:** Upload `deliverables/rest-techdebt-done.png` - shows "Setup the development environment" in the **Done** column.

---

## Task 9
**Answer:** Upload `deliverables/read-accounts.png` - shows "Read an account from the service" in the **Done** column.

---

## Task 10
**Answer:** Upload `deliverables/list-accounts.png` - shows "List all accounts in the service" in the **Done** column.

---

## Task 11
**Answer:** Upload `deliverables/update-accounts.png` - shows "Update an account in the service" in the **Done** column.

---

## Task 12
**Answer:** Upload `deliverables/delete-accounts.png` - shows "Delete an account from the service" in the **Done** column.

---

## Task 13 (CREATE)
```text
$ curl -s -i -X POST http://localhost:8080/accounts \
  -H "Content-Type: application/json" \
  -d '{"name": "John Doe", "email": "john.doe@example.com", "address": "123 Main Street, Springfield", "phone_number": "555-123-4567", "date_joined": "2026-11-09"}' 

HTTP/1.1 201 CREATED
Server: gunicorn
Date: Mon, 09 Nov 2026 08:35:46 GMT
Connection: close
Content-Type: application/json
Content-Length: 156
Location: http://localhost:8080/accounts/1
Access-Control-Allow-Origin: *
Permissions-Policy: interest-cohort=()
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin

{"address":"123 Main Street, Springfield","date_joined":"2026-11-09","email":"john.doe@example.com","id":1,"name":"John Doe","phone_number":"555-123-4567"}
```

---

## Task 14 (LIST)
```text
$ curl -s http://localhost:8080/accounts | python -m json.tool

[
    {
        "address": "123 Main Street, Springfield",
        "date_joined": "2026-11-09",
        "email": "john.doe@example.com",
        "id": 1,
        "name": "John Doe",
        "phone_number": "555-123-4567"
    }
]
```

---

## Task 15 (READ)
```text
$ curl -s http://localhost:8080/accounts/1 | python -m json.tool

{
    "address": "123 Main Street, Springfield",
    "date_joined": "2026-11-09",
    "email": "john.doe@example.com",
    "id": 1,
    "name": "John Doe",
    "phone_number": "555-123-4567"
}
```

---

## Task 16 (UPDATE)
```text
$ curl -s -i -X PUT http://localhost:8080/accounts/1 \
  -H "Content-Type: application/json" \
  -d '{"name": "John Doe", "email": "john.doe@example.com", "address": "456 Oak Avenue, Springfield", "phone_number": "555-987-6543", "date_joined": "2026-11-09"}' 

HTTP/1.1 200 OK
Server: gunicorn
Date: Mon, 09 Nov 2026 08:35:46 GMT
Connection: close
Content-Type: application/json
Content-Length: 155
Access-Control-Allow-Origin: *
Permissions-Policy: interest-cohort=()
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin

{"address":"456 Oak Avenue, Springfield","date_joined":"2026-11-09","email":"john.doe@example.com","id":1,"name":"John Doe","phone_number":"555-987-6543"}
```

---

## Task 17 (DELETE)
```text
$ curl -s -i -X DELETE http://localhost:8080/accounts/1

HTTP/1.1 204 NO CONTENT
Server: gunicorn
Date: Mon, 09 Nov 2026 08:35:46 GMT
Connection: close
Content-Type: text/html; charset=utf-8
Access-Control-Allow-Origin: *
Permissions-Policy: interest-cohort=()
X-Frame-Options: SAMEORIGIN
X-XSS-Protection: 1; mode=block
X-Content-Type-Options: nosniff
Referrer-Policy: strict-origin-when-cross-origin
```

---

## Task 18
**Answer:** Upload `deliverables/sprint2-plan.png` - shows the two Sprint 2 stories in the **Sprint backlog**.

---

## Task 19
**Answer:** Upload `deliverables/ci-workflow-done.txt`. It is the full GitHub Actions log for workflow run **42586582619**, showing every step succeeded:

```text
Checkout code                         success
Install dependencies                  success
Lint with flake8                      success
Run unit tests with nosetests         success
```

---

## Task 20
**Answer:** Upload `deliverables/ci-kanban-done.png` - shows "Need the ability to automate continuous integration checks" in the **Done** column.

---

## Task 21
**Answer (ci-build.yaml URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/.github/workflows/ci-build.yaml

The workflow checks out the code, installs dependencies, lints with flake8, and runs unit tests with nosetests against a `postgres:alpine` service.

---

## Task 22
**Answer (__init__.py URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/service/__init__.py

It configures `Talisman(app, content_security_policy=None, force_https=False)` for security headers and `CORS(app)` for CORS policies.

---

## Task 23
**Answer:** Upload `deliverables/security-headers-done.txt`. The test suite passes with CORS and security headers enabled:

```text
  0   100%
service/common/error_handlers.py      32      6    81%   46-48, 76-78
service/common/log_handlers.py        10      1    90%   21
service/common/status.py              46      0   100%
service/config.py                     11      5    55%   12-16
service/models.py                     69      3    96%   32, 98, 127
service/routes.py                     57      0   100%
----------------------------------------------------------------
TOTAL                                254     18    93%
----------------------------------------------------------------------
Ran 26 tests in 2.133s

OK
```

---

## Task 24
**Answer:** Upload `deliverables/security-kanban-done.png` - shows "Need to add security headers and CORS policies" in the **Done** column.

---

## Task 25
**Answer:** Upload `deliverables/sprint3-plan.png` - shows the three Sprint 3 stories in the **Sprint backlog**.

---

## Task 26
**Answer (application JSON at http://localhost:8080/):**
```json
{"name":"Account REST API Service","paths":"http://localhost:8080/accounts","version":"1.0"}
```

---

## Task 27
**Answer:** Upload `deliverables/kube-docker-done.png` - shows "Containerize your microservice using Docker" in the **Done** column.

---

## Task 28
**Answer:** Upload `deliverables/kube-kubernetes-done.png` - shows "Deploy your Docker image to Kubernetes" in the **Done** column.

---

## Task 29
**Answer (Dockerfile URL):**
https://github.com/yaqyn/devops-capstone-project/blob/main/Dockerfile

---

## Task 30
**Answer (Docker image details):**
```text
REPOSITORY   TAG       IMAGE ID       CREATED AT                      SIZE
accounts     1.0       5efdf77c8ea8   2026-11-09 11:37:18 +0300 +03   358MB
```

---

## Task 31
**Answer (deployment details):**
```text
NAME                            READY   STATUS    RESTARTS   AGE     IP             NODE       NOMINATED NODE   READINESS GATES
pod/accounts-7cc9867648-v7pg7   1/1     Running   0          84s     10.244.1.0     minikube   <none>           <none>
pod/postgres-7c8549989b-5xlhm   1/1     Running   0          2m39s   10.244.0.254   minikube   <none>           <none>

NAME               TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE   SELECTOR
service/accounts   ClusterIP   10.110.16.202   <none>        8080/TCP   26h   app=accounts
service/postgres   ClusterIP   10.104.103.73   <none>        5432/TCP   26h   app=postgres

NAME                       READY   UP-TO-DATE   AVAILABLE   AGE   CONTAINERS   IMAGES            SELECTOR
deployment.apps/accounts   1/1     1            1           26h   accounts     accounts:1.0      app=accounts
deployment.apps/postgres   1/1     1            1           26h   postgres     postgres:alpine   app=postgres

NAME                                  DESIRED   CURRENT   READY   AGE   CONTAINERS   IMAGES            SELECTOR
replicaset.apps/accounts-7cc9867648   1         1         1       84s   accounts     accounts:1.0      app=accounts,pod-template-hash=7cc9867648
replicaset.apps/accounts-86749f5899   0         0         0       26h   accounts     accounts:1.0      app=accounts,pod-template-hash=86749f5899
replicaset.apps/postgres-7c8549989b   1         1         1       26h   postgres     postgres:alpine   app=postgres,pod-template-hash=7c8549989b
```

---

## Task 32
**Answer (full Tekton pipeline run log is in `deliverables/pipelinerun.txt`):**
```text
PipelineRun: cd-pipeline-run-accounts
Pipeline: cd-pipeline
Namespace: capstone
Status: Succeeded
Tasks: init, clone, lint, tests, build, deploy


[init : remove] 2026-11-10T11:13:26Z echo "Removing all files from workspace ..."

[init : remove] 2026-11-10T11:13:26Z rm -rf ${WORKSPACE_SOURCE_PATH:?}/*
Workspace cleaned

[clone : clone] 2026-11-10T11:13:26Z git clone https://github.com/yaqyn/devops-capstone-project.git /workspace/source
Cloning into '/workspace/source'...
d446d79 fix: use ClusterIP service and portable Tekton deploy task

[lint : flake8] 2026-11-10T11:13:30Z flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
0
0
Linting passed.

[tests : nosetests] 2026-11-10T11:13:30Z nosetests -v --with-spec --spec-color --with-coverage --cover-package=service
nose.config: INFO: Ignoring files matching ['^\\.', '^_', '^setup\\.py$']
nose.plugins.cover: INFO: Coverage report will include only packages: ['service', 'service']

Test Flask CLI Commands
[1;32m- It should call the db-create command[1;0m

Test Cases for Account Model
[1;32m- It should Create an account and add it to the database[1;0m
[1;32m- It should Create an Account and assert that it exists[1;0m
[1;32m- It should Delete an account from the database[1;0m
[1;32m- It should Deserialize an account[1;0m
[1;32m- It should not Deserialize an account with a KeyError[1;0m
[1;32m- It should not Deserialize an account with a TypeError[1;0m
[1;32m- It should Find an Account by name[1;0m
[1;32m- It should List all Accounts in the database[1;0m
[1;32m- It should Read an account[1;0m
[1;32m- It should Serialize an account[1;0m
[1;32m- It should Update an account[1;0m

Account Service Tests
[1;32m- It should not Create an Account when sending the wrong data[1;0m
[1;32m- It should Create a new Account[1;0m
[1;32m- It should Delete an Account[1;0m
[1;32m- It should be idempotent when deleting a missing Account[1;0m
[1;32m- It should Read a single Account[1;0m
[1;32m- It should not Read an Account that does not exist[1;0m
[1;32m- It should be healthy[1;0m
[1;32m- It should get 200_OK from the Home Page[1;0m
[1;32m- It should List all Accounts[1;0m
[1;32m- It should return secure headers and a CORS policy[1;0m
[1;32m- It should not Create an Account when sending the wrong media type[1;0m
[1;32m- It should Update an existing Account[1;0m
[1;32m- It should not Update an Account with the wrong media type[1;0m
[1;32m- It should not Update an Account that does not exist[1;0m

Name                               Stmts   Miss  Cover   Missing
----------------------------------------------------------------
service/__init__.py                   22      3    86%   40-43
service/common/__init__.py             0      0   100%
service/common/cli_commands.py         7      0   100%
service/common/error_handlers.py      32      6    81%   46-48, 76-78
service/common/log_handlers.py        10      1    90%   21
service/common/status.py              46      0   100%
service/config.py                     11      5    55%   12-16
service/models.py                     69      3    96%   32, 98, 127
service/routes.py                     57      0   100%
----------------------------------------------------------------
TOTAL                                254     18    93%
----------------------------------------------------------------------
Ran 26 tests in 0.912s

OK

All tests passed.

[build : build] 2026-11-10T11:13:32Z buildah bud --format=oci --tls-verify=false -f ./Dockerfile -t accounts:1.0 .
#0 building with "default" instance using docker driver

#1 [internal] load build definition from Dockerfile
#1 transferring dockerfile: 532B done
#1 DONE 0.1s

#2 [internal] load metadata for docker.io/library/python:3.9-slim
#2 DONE 0.1s

#3 [internal] load .dockerignore
#3 transferring context: 2B done
#3 DONE 0.1s

#4 [internal] load build context
#4 DONE 0.0s

#5 [1/6] FROM docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b
#5 resolve docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b
#5 resolve docker.io/library/python:3.9-slim@sha256:2d97f6910b16bd338d3060f261f53f144965f755599aab1acda1e13cf1731b1b 0.1s done
#5 DONE 0.1s

#4 [internal] load build context
#4 transferring context: 42.51kB done
#4 DONE 0.1s

#6 [2/6] WORKDIR /app
#6 CACHED

#7 [3/6] COPY requirements.txt .
#7 CACHED

#8 [4/6] RUN python -m pip install -U pip wheel &&     pip install -r requirements.txt
#8 CACHED

#9 [5/6] COPY service ./service
#9 DONE 1.8s

#10 [6/6] RUN useradd -m -r service &&     chown -R service:service /app
#10 DONE 1.0s

#11 exporting to image
#11 exporting layers
#11 exporting layers 0.4s done
#11 exporting manifest sha256:623221b1484c7b5accd081e4d019d5ea11e805a3d393ccdabffd4bf7e85b72f7 0.0s done
#11 exporting config sha256:7e82bc6ee1368c12694347b98fbf09fc40ccd40db601bc3dde488a9d783021fe 0.0s done
#11 exporting attestation manifest sha256:30f55d12b2a52bb6d541ed36ecd96b7ebf1af78c482b0694f4b39c0e626ee7d0 0.0s done
#11 exporting manifest list sha256:c6fae4417c4b4e8fc879fb912facfe7abaceeba4c4403d0d3e5a8162f7e50397
#11 exporting manifest list sha256:c6fae4417c4b4e8fc879fb912facfe7abaceeba4c4403d0d3e5a8162f7e50397 0.0s done
#11 naming to docker.io/library/accounts:1.0 done
#11 unpacking to docker.io/library/accounts:1.0 0.1s done
#11 DONE 0.7s

 [33m1 warning found (use docker --debug to expand):
[0m - LegacyKeyValueFormat: "ENV key=value" should be used instead of legacy "ENV key value" format (line 20)
Successfully built accounts:1.0

[deploy : apply] 2026-11-10T11:13:36Z kubectl apply -f deploy/postgres.yaml && kubectl apply -f deploy/accounts.yaml
deployment.apps/postgres unchanged
service/postgres unchanged
deployment.apps/accounts unchanged
service/accounts unchanged
deployment "postgres" successfully rolled out
deployment "accounts" successfully rolled out
NAME                            READY   STATUS    RESTARTS   AGE
pod/accounts-7cc9867648-v7pg7   1/1     Running   0          74s
pod/postgres-7c8549989b-5xlhm   1/1     Running   0          2m29s

NAME               TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)    AGE
service/accounts   ClusterIP   10.110.16.202   <none>        8080/TCP   26h
service/postgres   ClusterIP   10.104.103.73   <none>        5432/TCP   26h

NAME                       READY   UP-TO-DATE   AVAILABLE   AGE
deployment.apps/accounts   1/1     1            1           26h
deployment.apps/postgres   1/1     1            1           26h

NAME                                  DESIRED   CURRENT   READY   AGE
replicaset.apps/accounts-7cc9867648   1         1         1       74s
replicaset.apps/accounts-86749f5899   0         0         0       26h
replicaset.apps/postgres-7c8549989b   1         1         1       26h

PipelineRun cd-pipeline-run-accounts completed successfully.
```

---

## Task 33
**Answer:** Upload `deliverables/cd-pipeline-done.png` - shows "Create a CD pipeline to automate deployment to Kubernetes" in the **Done** column after the CD pipeline deployment.
