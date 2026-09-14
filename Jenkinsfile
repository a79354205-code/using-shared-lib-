// =================================================================================
// Method 1: Global Pipeline Library (Recommended if configured in Jenkins)
// Make sure 'shared-lib' is added in:
// Manage Jenkins -> System -> Global Pipeline Libraries
// =================================================================================
@Library('shared-lib') _

// Calls vars/vpc.groovy from https://github.com/a79354205-code/shared-lib
// It executes:
//   1. Stage 'Checkout' (checks out this repository from SCM)
//   2. Stage 'VPC' (provisions/echoes VPC creation)
vpc()

// ---------------------------------------------------------------------------------
// Alternative Usages:
//
// 1. Pass a custom VPC name:
//    vpc('prod-vpc')
//    or: vpc(name: 'prod-vpc')
//
// 2. Dynamic loading without configuring Jenkins Global Pipeline Libraries:
//    /*
//    library identifier: 'shared-lib@main', retriever: modernSCM(
//        [$class: 'GitSCMSource',
//         remote: 'https://github.com/a79354205-code/shared-lib.git']
//    )
//    vpc()
//    */
// =================================================================================
