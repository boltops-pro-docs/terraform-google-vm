<!-- note marker start -->
**NOTE**: This repo contains only the documentation for the private BoltsOps Pro repo code.
Original file: https://github.com/boltopspro/terraform-google-vm/blob/master/README.md
The docs are publish so they are available for interested customers.
For access to the source code, you must be a paying BoltOps Pro subscriber.
If are interested, you can contact us at contact@boltops.com or https://www.boltops.com

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
