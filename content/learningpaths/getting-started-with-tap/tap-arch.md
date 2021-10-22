---
title: Tanzu Application Platform
# draft: true
weight: 1
layout: single
team:
  - VMware Tanzu
---

## Outcomes

After completing the lesson you will ...

## Lesson

### Architecture Overview

Here is a simplified description of TAP architecture:

_NOTES:
- [This Slack thread](https://vmware.slack.com/archives/C01V8EAS5BN/p1634044519465000) contains a discussion about architecture diagrams and how the TAP team is attempting to come up with material. Hopefully we can use the output of that team here._
- Also from the above Slack thread, further down:
  - <https://vmware.slack.com/archives/C0262MBRGFM/p1634844438006400?thread_ts=1633640105.374900&cid=C0262MBRGFM>
  - This diagram has a bunch of good stuff <https://files.slack.com/files-pri/T8YCM8N9L-F02J8GMLTLG/tanzu-overview-excalidraw.png>

Using the above diagram as reference, here is a narration of the components of TAP and what they do,
approximately in the order they are used in the lifecycle of an app develop/build/deploy:

At the highest level, a TAP installation lives in a single Kubernetes cluster. It's really a collection of packages:
- Application Accelerator - Quote from Alex Barbato: "Codify defaults for your organization". Templates for configuration, pipelines, code, security, observability ... whatever is important that you don't want to reinvent, or want to standardize across your organization.
- Developer Conventions - Tools for developer productivity: e.g., Live reload, debugging in the cluster.
- Build Service - Make me a container for my app code o run in, please. Built on OSS Cloud Native Build Packs.
- Cloud Native Runtimes - Higher-level abstractions over Kubernetes objects, plus other capabilities.
- Convention Service - Automatically do the work necessary to make an application "just work" in Kubernetes.  Feels to me like an extension of a buildpack, for runtime.
- Supply Chain Choreographer - Declarative Pipeline without the implementation. Built on OSS Cartographer.
- Supply Chain Security Tools - build-time security scans and related things.
- Application Live View - Observability Lite. For now, expose OSS Spring Boot Actuator data. Question: does this include logs?
- Services Toolkit - External service catalog. Think `cf services` from TAS/PCF. Built on OSS service bindings for k8s.
- API Portal - API catalog. Built on OSS Spring Cloud Gateway.
