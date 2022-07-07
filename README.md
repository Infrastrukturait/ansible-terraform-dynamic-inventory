
# Dynamic ansible inventory from tfstate

[![WeSupportUkraine](https://raw.githubusercontent.com/Infrastrukturait/WeSupportUkraine/main/banner.svg)](https://github.com/Infrastrukturait/WeSupportUkraine)
An Ansible [dynamic inventory](http://docs.ansible.com/ansible/latest/intro_dynamic_inventory.html) script to process Terraform state and return
Ansible host data from [Terraform Provider for Ansible](https://github.com/nbering/terraform-provider-ansible/) host resources. See the
Terraform Provider for it's own installation and use.

## Prologue
### Why a Fork?
This is for from [nbering/terraform-inventory](https://github.com/nbering/terraform-inventory) because it does not appear to be maintained, and I wanted to add support to
python3 to make it work with [ansible <= 2.5](https://docs.ansible.com/ansible/latest/reference_appendices/python_3_support.html).

## Usage
Copy the [terraform.py](./terraform.py) script file to a location on your system. Ansible's own documentation suggests the location `/etc/ansible/terraform.py`,
but the particular location does not matter to the script. Ensure it has executable permissions (`chmod +x /etc/ansible/terraform.py`).
With your Ansible playbook and Terraform configuration in the same directory, run Ansible with the `-i` flag to set the inventory source.
```
$ ansible-playbook -i /etc/ansible/terraform.py playbook.yml
```

## Environment Variables


### ANSIBLE TF BIN

Override the path to the Terraform command executable. This is useful if you have multiple copies or versions installed and need to specify a specific binary.
The inventory script runs the `terraform state pull` command to fetch the Terraform state, so that remote state will be fetched seemlessly regardless of the backend configuration.


### ANSIBLE TF DIR

Set the working directory for the `terraform` command when the scripts shells out to it. This is useful if you keep your terraform and ansible configuration in separate directories. Defaults to using the current working directory.


### ANSIBLE TF WS NAME

Sets the workspace for the `terraform` command when the scripts shells out to it, defaults to `default` workspace - if you don't use workspaces this is the one you'll be using.


## License

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

```text
The MIT License (MIT)

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.

Source: <https://opensource.org/licenses/MIT>
```
## Authors
-  Nicholas Bering | [website](https://nicholasbering.ca/) | [email](mailto:bering.nicholas@gmail.com) | [github](https://github.com/nbering)
- Rafał Masiarek | [website](https://masiarek.pl) | [email](mailto:rafal@masiarek.pl) | [github](https://github.com/rafalmasiarek)
