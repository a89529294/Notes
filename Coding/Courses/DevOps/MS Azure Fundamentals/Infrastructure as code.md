Infrastructure as code is a concept where you _manage your infrastructure as lines of code_.
At an introductory level, it's things like using _Azure Cloud Shell, Azure PowerShell, or the Azure CLI_ to manage and configure your resources.
_ARM templates_ and _Bicep_ are two examples of using infrastructure as code with the Azure Resource Manager to maintain your environment.

## ARM templates
By using ARM templates, you can describe the resources you want to use in a _declarative JSON format_. With an ARM template, the deployment code is verified before any code is run. This ensures that the resources will be created and connected correctly. The template then orchestrates the creation of those resources in parallel. That is, if you need 50 instances of the same resource, all 50 instances are created at the same time.

## Bicep
Bicep is a language that uses declarative syntax to deploy Azure resources. A Bicep file defines the infrastructure and configuration. Then, ARM deploys that environment based on your Bicep file. _While similar to an ARM template, which is written in JSON, Bicep files tend to use a simpler, more concise style_.

