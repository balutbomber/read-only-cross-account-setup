# read-only-cross-account-role


The **read-only-cross-account-role** template creates a single role with the AWS ReadOnlyAccess policy attached to it.  Users from the Federation Account represented can assume this role.

## Deployment Location

This template **MUST** be executed in each sub account.  It provides the read only role which a federated user will assume in the account.


## Usage

`aws cloudformation deploy --template-file ./src/cfn/roots/read-only-cross-account-role/main.yml --stack-name oncore-otc-readonly-role --profile named_profile --capabilities CAPABILITY_NAMED_IAM --parameter-overrides FederationAccountId=federation_account_id Stage=prod Tag=oncore-otc`


* **federation\_account\_id** the AWS account id of the account where the IAM users reside.

**NOTE** --parameter-overrides can be ommited if updating the stack and **federation\_account\_id** has not changed.

* **named_profile** - the named profile of the aws account being deployed to
* **the_stage** - the name of the stage deploying to. eg. dev | test | prod
* **the_tag** - the tag for the deployment.  eg. oncore-otc


## Roles
### ReadOnlyRole

This role gives read only access to the console for users assuming this role from the federation account.

Users must have **mfa** enabled on their iam user in the federation account to successfully assume this role.
