# Using Shared Library - VPC Test Pipeline

This repository tests the VPC pipeline defined in [a79354205-code/shared-lib](https://github.com/a79354205-code/shared-lib).

## How it Works

The shared library contains `vars/vpc.groovy`:
```groovy
def call(String vpcName = 'my-vpc') {
    pipeline {
        agent any
        stages {
            stage('VPC') {
                steps {
                    echo "Creating VPC: ${vpcName}..."
                    sh "echo 'VPC ${vpcName} created successfully'"
                }
            }
        }
    }
}
```

Since `vpc.groovy` defines the whole declarative pipeline, `Jenkinsfile` simply loads the library and invokes `vpc()`:

```groovy
@Library('shared-lib') _

vpc()
```

To test with a custom VPC name:
```groovy
@Library('shared-lib') _

vpc('my-custom-vpc')
```

## Jenkins Configuration
1. Go to **Manage Jenkins** &rarr; **System** &rarr; **Global Pipeline Libraries**.
2. Add a new library:
   - **Name**: `shared-lib`
   - **Default version**: `main`
   - **Retrieval method**: Modern SCM &rarr; Git &rarr; `https://github.com/a79354205-code/shared-lib.git`
3. Create a Pipeline Job pointing to this repository (`https://github.com/a79354205-code/using-shared-lib-`).
