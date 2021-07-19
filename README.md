# deploy_template
template for auto provision gcp resources via deployment manager and terraform

## how to run

> deployment manager

```
gcloud deployment-manager deployments create gcpnet --config=config.yaml

## if something goes wrong, need to delete deployment manager configuration before deploying it again
gcloud deployment-manager deployments delete gcpnet
```

> terraform

```
terraform ini

## create an execution plan
terraform plan
## confirmed the planned action
terraform apply

```

## introduction

- Deployment Manager allows you to use Python or Jinja2 templates to parameterize your configuration. This allows you to reuse common deployment paradigms such as networks, firewall rules, and VM instances. Start by creating templates for an auto-mode network and a custom-mode network.

- Terraform enables you to safely and predictably create, change, and improve infrastructure. It is an open-source tool that codifies APIs into declarative configuration files that can be shared among team members, treated as code, edited, reviewed, and versioned.


