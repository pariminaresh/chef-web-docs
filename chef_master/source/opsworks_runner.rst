=====================================================
Adding a Runner to Opsworks for Chef Automate
=====================================================
`[edit on GitHub] <https://github.com/chef/chef-web-docs/blob/master/chef_master/source/opsworks_runner.rst>`__

This section describes the steps to add a Runner to your instance of Opsworks for Chef Automate.

.. note:: Make sure you have selected "Use an existing EC2 key pair" in the "Select an SSH key" section while creating your Opsworks for Chef Automate instance.

#. After creating you Chef Automate instance download the "Starter Kit" and unzip it. It will unzip into a directory like ``chef-automate-an1leihp6urosoui`` where ``chef-automate`` is the name you have given you your instance.
#. Create a VM that is accessible from the Chef Automate instance via SSH. There are multiple ways of doing this but here is an example to do it with ``knife-ec2`` You can get the values for subnet_id, security_group_id and ssh_key_name from AWS Management Console:

  .. code-block:: bash

    knife ec2 server create \
      --aws-profile chef-aws \
      --aws-credential-file ~/.aws/credentials \
      --region us-east-1 \
      --subnet <subnet_id> \
      --security-group-ids <security_group_id> \
      --ssh-key <ssh_key_name> \
      --flavor t2.micro \
      --image ami-42d6fb55 \
      --no-bootstrap

#. ssh into Opsworks Chef Automate instance

  .. code-block:: bash

    ssh ec2-user@chef-automate-an1leihp6urosoui.gamma.opsworks-cm.io

#. Register the VM you have created as a runner:

  .. code-block:: bash

    sudo delivery-ctl install-runner \
      <fqdn_of_the_machine> \
      <ubuntu || ec2-user> \
      --ssh-identity-file /home/ec2-user/builder.pem

#. Verify your runner's status for Chef Automate console

  Chef Automate Console -> Runners -> Manage Runners -> Test

  Chef Automate Console link will be something like https://chef-automate-an1leihp6urosoui.gamma.opsworks-cm.io/e/default/#/dashboard
