# read-only-iam-group


The **read-only-iam-group** template creates a group giving users read only access to a specified sub account.

## Deployment Location

This template **MUST ONLY** be executed in the account where the IAM users exist.

Once this template is run, add any IAM users to the group which need read only access into the sub account.

## Groups

* **CrossAccountReadOnlyGroup** This group allows users to assume the read only role in sub account.

## Usage

`aws cloudformation deploy --template-file ./src/cfn/roots/read-only-iam-group/main.yml --stack-name oncore-otc-readonly-group --capabilities CAPABILITY_NAMED_IAM --parameter-overrides SubAccountId=sub_account_id Stage=prod Tag=oncore-otc`


* **sub\_account\_id** the AWS account id of the account where users will assume the read only role.

**NOTE** --parameter-overrides can be ommited if updating the stack and **sub\_account\_id** has not changed.

* **the_stage** - the name of the stage deploying to. eg. dev | test | prod
* **the_tag** - the tag for the deployment.  eg. oncore-otc


