<!-- note marker start -->
NOTE: This repo contains only the documentation for the private BoltsOps repo code.
Original file: https://github.com/boltops-pro/terraform-google-vm/blob/master/README.md
The docs are publish so they are available for interested subscribers.
For access to the source code, you can become a BoltOps subscriber.
See: https://learn.boltops.com

<!-- note marker end -->

## VM Demos

Configure tfvars for the vm stack.

    app/stacks/vm/tfvars
    └── dev
        ├── base.tfvars
        ├── ubuntu.tfvars
        └── windows.tfvars

The tfvars structure leverages the [Terraspace Instance Option](https://terraspace.cloud/docs/tfvars/instance-option/) to use the same code to create different VM servers.

We'll create an example 1) windows and 2) ubuntu server

    terraspace up vm -i ubuntu
    terraspace up vm -i windows

![](https://img.boltops.com/images/modules/vm/vm.png)

Add more tfvars files to create more stateful VM servers with different settings.

## base.tfvars instance option

The way the instance optoin is being used in the tfvars is worth nothing. The `base.tfvars` file makes use `options[:instance]` to set the name of the instance.

app/stacks/vm/tfvars/dev/base.tfvars

    name        = "<%= options[:instance] || "vm" %>"

This means the instance name will match the `-i ubuntu` option passed in the CLI.
