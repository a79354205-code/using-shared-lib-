// Load the shared library configured in Jenkins (Manage Jenkins -> System -> Global Pipeline Libraries)
// Replace 'shared-lib' with the library name you configured in Jenkins, or use @Library('shared-lib@main') _
@Library('shared-lib') _

// vars/vpc.groovy in a79354205-code/shared-lib defines the entire pipeline.
// Default VPC name is 'my-vpc'
vpc()

// To specify a custom VPC name, you can pass it as a parameter:
// vpc('production-vpc')
