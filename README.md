# Crossplane

Terraform module which configure Crossplane resources on Amazon AWS

## Usage

```hcl
module "crossplane" {
  source  = "nlamirault/crossplane/aws"
  version = "x.y.z"

  cluster_name = var.cluster_name

  namespace       = var.namespace
  service_account = var.service_account

  tags = var.tags
}
```

and variables :

```hcl
cluster_name = "foo-staging-eks"

namespace       = "crossplane-system"
service_account = "provider-aws"

tags = {
    "project" = "foo"
    "env"     = "staging"
    "service" = "crossplane"
    "made-by" = "terraform"
}
```

## Documentation

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
## Requirements

| Name | Version |
|------|---------|
| <a name="requirement_terraform"></a> [terraform](#requirement\_terraform) | >= 1.0.0 |
| <a name="requirement_aws"></a> [aws](#requirement\_aws) | >= 3.14.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_aws"></a> [aws](#provider\_aws) | 4.5.0 |

## Modules

| Name | Source | Version |
|------|--------|---------|
| <a name="module_crossplane_role"></a> [crossplane\_role](#module\_crossplane\_role) | terraform-aws-modules/iam/aws//modules/iam-assumable-role-with-oidc | 4.14.0 |

## Resources

| Name | Type |
|------|------|
| [aws_iam_policy.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/iam_policy) | resource |
| [aws_eks_cluster.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/eks_cluster) | data source |
| [aws_iam_policy_document.this](https://registry.terraform.io/providers/hashicorp/aws/latest/docs/data-sources/iam_policy_document) | data source |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| <a name="input_cluster_name"></a> [cluster\_name](#input\_cluster\_name) | Name of the EKS cluster | `string` | n/a | yes |
| <a name="input_namespace"></a> [namespace](#input\_namespace) | The Kubernetes namespace | `string` | `"crossplane-system"` | no |
| <a name="input_service_account"></a> [service\_account](#input\_service\_account) | The Kubernetes service account | `string` | `"provider-aws"` | no |
| <a name="input_tags"></a> [tags](#input\_tags) | Tags for AWS resources | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| <a name="output_role_arn"></a> [role\_arn](#output\_role\_arn) | Amazon Resource Name for Crossplane |
<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
