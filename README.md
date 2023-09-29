# Terraform Module for Azure Key Vault Secrets

a terraform module for generating key vault secrets

##  Usage

General usage for modules can be found here: https://developer.hashicorp.com/terraform/language/modules/sources#github

From the terraform code you want to consume one of these modules, place one or more of the following blocks. 

### certificate authority

```terraform
module "certificate_authority" {
  source = "github.com/ms-us-rcg-cloud-innovation/terraform-azure-key-vault-secrets//modules/key-vault-certificate-authority"
  
  name          = "ca"
  common_name   = "common_name"
  organization  = "organization"
    
  # azurerm_key_vault.example.id
  key_vault_id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.KeyVault/vaults/vault1"
}

```

### certificate

```terraform

module "certificate" {
  source = "github.com/ms-us-rcg-cloud-innovation/terraform-azure-key-vault-secrets//modules/key-vault-certificate"
  
  name = "name"
  common_name = "common_name"
  organization = "organization"
  
  # the name of the ca stored in the keyvault
  ca = "ca"
    
  # azurerm_key_vault.example.id
  key_vault_id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.KeyVault/vaults/vault1"
}
```

### password

```terraform
module "password" {
  source = "github.com/ms-us-rcg-cloud-innovation/terraform-azure-key-vault-secrets//modules/key-vault-password"
  
  name    = "name"
  length  = 16
  
  # azurerm_key_vault.example.id
  key_vault_id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.KeyVault/vaults/vault1"
}
```

### value 

```terraform
module "value" {
  source = "github.com/ms-us-rcg-cloud-innovation/terraform-azure-key-vault-secrets//modules/key-vault-value"
  
  name = "name"
  value = "value"
  
  # azurerm_key_vault.example.id
  key_vault_id = "/subscriptions/00000000-0000-0000-0000-000000000000/resourceGroups/mygroup1/providers/Microsoft.KeyVault/vaults/vault1"
}
```
