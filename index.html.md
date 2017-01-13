---
title: MongoDB for Pivotal Cloud Foundry
owner: London Services
---

This is documentation for the [MongoDB service](https://network.pivotal.io/products/p-mongodb) for [Pivotal Cloud Foundry](https://network.pivotal.io/products/pivotal-cf) (PCF).

<p class="note"><strong>Note</strong>:This product is no longer being maintained or updated with new versions, it has also been removed from Pivotal Network. If you require access to an older version of the product please contact Pivotal Support</p>

## Product snapshot

<dl>
<dt>Current MongoDB for PCF Details</dt>
<dd><strong>Version</strong>: 1.4.2 </dd>
<dd><strong>Release Date</strong>: 24th November 2015</dd>
<dd><strong>Software component version</strong>: MongoDB OSS 2.6.1</dd>
<dd><strong>Compatible Ops Manager Version(s)</strong>: 1.5.x, 1.4.x</dd>
<dd><strong>Compatible Elastic Runtime Version(s)</strong>: 1.5.x, 1.4.x</dd>
<dd><strong>vSphere support?</strong> Yes</dd>
<dd><strong>AWS support?</strong> Yes</dd>
<dd><strong>Openstack support?</strong> No</dd>
</dl>

## Upgrading to the Latest Version

Consider the following compatibility information before upgrading MongoDB for Pivotal Cloud Foundry.

<p class="note"><strong>Note</strong>: Before you upgrade to Ops Manager 1.4.x, you must first upgrade MongoDB for PCF to any version in its 1.3.x minor release. This allows MongoDB for PCF upgrades after you install OpsManager 1.4.x. </p>

For more information, refer to the full [Product Compatibility Matrix](../compatibility-matrix.pdf).

<table border="1" class="nice">
<tr>
  <th>Ops Manager Version</th>
  <th>Supported Upgrades from Imported MongoDB Installation</th>
</tr>
<tr>
  <th>1.3.x</th>
  <td><ul>
      <li>From 1.3.2 to 1.3.3</li>
      <li>From 1.3.2 to 1.3.4.1</li>
      <li>From 1.3.3 to 1.3.4.1</li>
    </ul>
  </td>
</tr>
<tr>
  <th>1.6.x, 1.5.x and 1.4.x</th>
  <td><ul>
      <li>From 1.3.2 to 1.4.0, 1.4.1, 1.4.2</li>
      <li>From 1.3.3 to 1.4.0, 1.4.1. 1.4.2</li>
      <li>From 1.3.4.1 to 1.4.0, 1.4.1, 1.4.2</li>
      <li>From 1.4.0 to 1.4.1, 1.4.2</li>
      <li>From 1.4.1 to 1.4.2</li>
    </ul>
  </td>
</tr>
</table>

### Install via Pivotal Operations Manager

To install MongoDB for PCF, follow the procedure for installing Pivotal Cloud Foundry Operations Manager tiles:

1. Download the product file from [Pivotal Network](https://network.pivotal.io/).
1. Upload the product file to your Ops Manager installation.
1. Click **Add** next to the uploaded product description in the Available Products view to add this product to your staging area.
1. Click the newly added tile to review any configurable options.
1. Click **Apply Changes** to install the service.

### Provisioning and Binding via Cloud Foundry

Once you have installed the product, it automatically registers itself with your Elastic Runtime. At this point, the product is available to your application developers, either in the Marketplace in Apps Manager, or via `cf marketplace`. They can add, provision, and bind the service to their applications like any other CF service:

```
$ cf create-service p-mongodb development mongodb
$ cf bind-service my-application mongodb
$ cf restart my-application
```

### Example Application

To help your application developers get started with MongoDB for PCF, we have provided an [example application](https://github.com/pivotal-cf/cf-mongodb-example-app/archive/master.zip).

### Available Plans

Currently, the only available plan is the **development** plan. This plan provisions a single MongoDB collection, suitable for development workloads.

We **do not** recommend using this plan in a production environment.

### Known Limitations

Limitations with the current MongoDB product include:

* It cannot be scaled beyond a single virtual machine.
* It has no backup and restore capabilities.
* Users cannot provision multiple collections in a single service instance,
  though they can easily provision multiple instances, each with their own
  collection.
* Constraining CPU, memory and/or disk usage is not supported.

We plan to address all of these limitations in future releases.

### Feedback

Please provide any bugs, feature requests, or questions to [the Pivotal Cloud Foundry Feedback list](mailto:pivotal-cf-feedback@pivotal.io).

### Further Reading

* [Official MongoDB Documentation](http://docs.mongodb.org/manual/)
