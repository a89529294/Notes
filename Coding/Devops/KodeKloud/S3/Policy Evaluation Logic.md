When a principal tries to use the _AWS Management Console_, the _AWS API_, or the _AWS CLI_, that principal sends a _request_ to AWS. When an AWS service receives the request, AWS completes several steps to determine whether to allow or deny the request.

1. **Authentication** – AWS first authenticates the principal that makes the request, _if necessary_. This step is not necessary for a few services, such as Amazon S3, that allow some requests from anonymous users.
2. **[Processing the request context](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic_policy-eval-reqcontext.html)** – AWS processes the information gathered in the request to determine which policies apply to the request.
3. **[How AWS enforcement code logic evaluates requests to allow or deny access](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_evaluation-logic_policy-eval-denyallow.html)** – AWS evaluates all of the policy types and the order of the policies affects how they are evaluated. AWS then processes the policies against the request context to determine whether the request is allowed or denied.

## __Evaluating identity-based policies with resource-based policies (same account)__

Identity-based policies and resource-based policies grant permissions to the identities or resources to which they are attached. _When an IAM entity (user or role) requests access to a resource within the same account_, AWS evaluates all the permissions granted by the identity-based and resource-based policies. _The resulting permissions are the union of the permissions of the two types_. If an action is allowed by an identity-based policy, a resource-based policy, or both, then AWS allows the action. An explicit deny in either of these policies overrides the allow.

## __Cross Account Policy Evaluation Logic__

You can allow a principal in one account to access resources in a second account. This is called cross-account access. When you allow cross-account access, the account where the principal exists is called the _trusted_ account. The account where the resource exists is the _trusting_ account.

To allow cross-account access, you attach a resource-based policy to the resource that you want to share. You must also attach an identity-based policy to the identity that acts as the principal in the request. The _resource-based policy in the trusting account must specify the principal of the trusted account that will have access to the resource_. You can specify the entire account or its IAM users, federated users, IAM roles, or assumed-role sessions. You can also specify an AWS service as a principal. For more information, see [How to specify a principal](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements_principal.html#Principal_specifying).

The principal's _identity-based policy must allow the requested access to the resource in the trusting service_. You can do this by specifying the ARN of the resource.

