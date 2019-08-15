

Google Cloud Platform consists of the following:
 * Compute Engine - Infrastructure as a Service (IaaS), VMs, good fit for existing systems, create a custom machine "shape"
 * App Engine - Platform as a Service (PaaS), make your web code run extremely well
 * Container Engine - Hosted Kubernetes
 * BigQuery - data warehouse for analytics, batch and streaming, columnar (AWS RedShift is a competitor)
 * Cloud Storage - object storage (in buckets?), has different access level classes


Projects
 * projects are a good way to separate cloud-computing services (by team or product for example.)


IAM
 * Primitive roles set project-level permissions
   * Viewer - read-only actions that don't affect state
   * Editor - permissions that modify state
   * Owner - manage roles and permissions for a project and resources within, billing


Cloudshell
  * `gcloud auth list`


Things to play with:
 * BigQuery GIS

Things to follow-up on:
 * Review column-orinted dbs
 * OLAP vs OLTP
 * Basic/NTLM auth


## References
 * Deciding between Compute Engine, Container Engine, App Engine https://www.youtube.com/watch?v=g0dN8Hkh5H8
