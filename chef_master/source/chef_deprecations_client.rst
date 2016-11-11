=====================================================
Chef Deprecation Warnings
=====================================================
`[edit on GitHub] <https://github.com/chef/chef-web-docs/blob/master/chef_master/source/chef_deprecations_client.rst>`__

.. tag client_deprecations

When we wish to remove a feature or an API in Chef, we try to first mark it with a deprecation warning that contains a link to a description of the change and how to fix it.

.. end_tag

Example
=====================================================

.. code-block:: ruby

   Deprecated features used!
     JSON auto inflation is not supported (CHEF-1) at (irb):7:in `irb_binding'.
     Please see https://docs.chef.io/chef-client/deprecations/json_auto_inflate.html for further details and information on how to correct this problem.

Fixing Deprecations
=====================================================

To test your code for deprecations, you can put Test Kitchen in a mode where any deprecations cause the chef run to fail. Ensure your ``.kitchen.yml`` includes:

.. code-block:: yaml

   provisioner:
     deprecations_as_errors: true

and then run Test Kitchen as usual. Test Kitchen will fail if any deprecations errors are issued.

All Deprecations
=====================================================

.. list-table::
  :widths: 50 350 50
  :header-rows: 1

  * - ID
    - Description
    - Version
  * - :doc: `CHEF-1 </deprecations_json_auto_inflate>`
    - Consumers of JSON are now required to be explicit in how it is turned in to a Chef object.
    - 12.7.2  
