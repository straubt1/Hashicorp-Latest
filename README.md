# Hashicorp-Latest

## Terraform-Core

Build the `master` branch of [Terraform Core](https://github.com/hashicorp/terraform) and make the binaries available for use.

Binaries saved to `/go/bin/terraform`.

Uses multi-stage dockerfile to generate the binaries, then copies them into a lightweight image.

Trying to build for the three main OS's but failing.
```docker
ENV XC_OS="linux darwin windows"
```

## Terraform-Provider-Azurerm

Build the `master` branch of [AzureRM Provider](https://github.com/terraform-providers/terraform-provider-azurerm) and make the binaries available for use.

Binaries saved to `/go/bin/terraform-provider-azurerm`.

## Terraform-Latest

A combination of both the latest of Terraform-Core and Terraform-Provider-Azurerm ready for use.

