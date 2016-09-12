---
title: On-demand Service Broker
owner: London Services Enablement
---

This guide is intended for people who want to author service tiles for Pivotal Cloud Foundry (PCF) using the On-demand Service Broker.

## <a id='overview'></a>Overview

PCF operators make software services such as databases available to developers by using the Ops Manager **Installation Dashboard** to install service tiles. Before Bosh 2.0, operators configured a service tile by pre-assigning a block of VMs with fixed CPU, hard disk, and RAM levels to allocate as instances for each service. This limited the possible number of instances and demanded wasteful one-size-fits-all resource provisioning.

On-demand services let you provision instances more flexibly. The operator does not pre-allocate a block of VMs for the instance pool, and they can specify an allowable range rather than fixed settings for instance resource levels. When a developer creates an on-demand service instance, they then provision it at creation time.

The on-demand services broker simplifies tile authoring, and is the standard approach for both Pivotal internal services teams and Pivotal partner independent software vendors (ISVs) to develop on-demand services for PCF.

The [About the On-demand Service Broker](./about.html) topic describes in greater detail how the on-demand service broker works within PCF.

## <a id='product-snapshot'></a>Product Snapshot

<dl>
<dt>Current On-demand Service Broker details:</dt>
<dd><strong>Version</strong>: 0.9.0</dd>
<dd><strong>Release date</strong>: 6 September 2016</dd>
<dd><strong>Compatible Ops Manager Version(s)</strong>: v1.8</dd>
<dd><strong>Compatible Elastic Runtime version(s)</strong>: v1.8</dd>
<dd><strong>vSphere support?</strong> Yes</dd>
<dd><strong>AWS support?</strong> Yes</dd>
</dl>

## <a id='new-features'></a>Key Features

The benefits of provisioning IaaS resources on-demand are:

* Scale resource consumption linearly with need, without having to plan for pre-provisioning.
* App developers get more control over resources, and do not have to do acquire them through the operator.

The benefits of using ODB to develop on-demand services are:

* ODB reduces the amount of code service developers have to write by abstracting away functionality common to most single-tenant on-demand service brokers.
* ODB uses BOSH to deploy service instances, so anything that is BOSH-deployable can integrate with Cloud Foundry's services marketplace.

ODB uses the following BOSH features:

* Dynamic IP management
* Availability zones
* Globally-defined resources (**Cloud Config**). This results in manifests that are portable across BOSH CPIs, and are substantially smaller than old-style manifests.
* Links between deployed BOSH instances consuming information, e.g. IP addresses, of other instances.

## <a id='prerequisites'></a>Prerequisites for deploying brokers that use ODB

Minimum versions of Cloud Foundry and BOSH are described in [the operator section](operating.html#configure-bosh).