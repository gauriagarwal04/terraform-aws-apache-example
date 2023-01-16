Teraform Module to provision an EC2 instance that is running Apache.

Not intended for production use. Just showcasing how to create a public module on terraform registry

```hcl
terraform {

}

provider "aws" {
  region = "us-east-1"
}

module "apache" {
  source        = ".//terraform-aws-apache-example"
  vpc_id        = "vpc-000000"
  public_key    = "ssh-rsa AAAAB......."
  instance_type = "t2.micro"
  server_name   = "Apache Example Server"
}

output "instance_ip_addr" {
  value = module.apache.instance_ip_addr
}
```