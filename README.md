# cross-account-setup

The **cross-account-setup** project contains cloudformation used to setup [cross account access](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_cross-account-with-roles.html) from the dev account into the production account.

	
There are 2 parts to setting up the cross account access:

1. A role with a read only policy in the production account which users can [assume](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_use.html).
2. A group in the dev account which member users can use to assume the read only role in the production account.

## Linting

Validation of CloudFormation templates is accomplished using [cfn-python-lint](https://github.com/aws-cloudformation/cfn-python-lint).

To lint the clouformation templates run the following command:

`cfn-lint`

## src/cfn/roots

`src/cfn/roots/` contains root cloudformation scripts.  These are the scripts which are deployed to needed accounts.

## Root Templates

Please read the documentation for each root template before deploying.

* [read-only-cross-account-role](./src/cfn/roots/read-only-cross-account-role/README.md)
* [read-only-iam-group](./src/cfn/roots/read-only-iam-group/README.md)