---

copyright:
  years: 2020
lastupdated: "2020-10-08"

keywords: couchdb, operator, release notes

subcollection: Cloudant

---

{:new_window: target="_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:deprecated: .deprecated}
{:external: target="_blank" .external}

<!-- Acrolinx: 2020-04-23 -->

# Release notes
{: #release-notes-couchdb-operator}

Changes and updates to Operator for Apache CouchDB that are grouped by version number.
{: shortdesc}

## v1.2.1 (15 September 2020)
{: #v1.2.1}

*Bug fixes*
 - Configuration files are incorrectly created with read-only file permissions.

## v1.2.0 (14 September 2020)
{: #v1.2.0}

Adds a number of configuration options to the search container, enabled via v1.5.0 of the management container.

This also fixes a performance regression in the search container caused by debug-level logging being enabled by default.

The following new, optional fields are added to the CouchDBCluster CRD:

 - `spec.environment.clouseau.logLevel`
 - `spec.environment.clouseau.maxIndexesOpen`
 - `spec.environment.clouseau.closeIfIdle`
 - `spec.environment.clouseau.idleCheckIntervalSecs`

*Bug fixes*
- CouchDB Search must not log at `DEBUG` level by default.

## v1.1.0 (17 August 2020)
{: #v1.1.0}

Adds more configuration for resource management, including the ability to set resource constraints on the CouchDB containers.

The following new, optional fields are added to the CouchDBCluster CRD:

 - `spec.securityContext`
 - `spec.resources`

*Enhancements*
 - Erlang scheduler count is based on the database container CPU requests, rounded up to the nearest integer.
 - Adds a liveness check so that search containers restart if they lose connectivity to the CouchDB node. This situation can happen if the CouchDB container is restarted by the OOMkiller.
 - JVM now uses cgroup aware memory settings.
 - Support CouchDBClusters deployed to the same namespace.
 - Changes to the CouchDBCluster CRD now propagate to CouchDB nodes without a manual pod restart.
 - Adds option to set resource constraints for CouchDB containers.
 - Adds option to set securityContext for the CouchDBCluster pods.

*Bug fixes*
 - Resource limits and requests propagate correctly to the search container.
