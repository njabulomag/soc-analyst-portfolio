# Manual Threat Intelligence Indicators

## Overview

This document describes the manual creation of Indicators of Compromise (IOCs) within Microsoft Sentinel Threat Intelligence. Three indicator types were created to demonstrate how security teams can build a centralized Threat Intelligence repository using the STIX 2.1 framework.

---

## Objective

The objective of this implementation was to manually create multiple IOC types that can later be used during threat detection, investigation, threat hunting, and incident response.

---

# Indicator 1 – Malicious IPv4 Address

## Observable Type

IPv4 Address

## Purpose

The IPv4 indicator represents a known malicious IP address that can be matched against security events generated within Microsoft Sentinel.

## Configuration

* Object Type: Indicator
* Observable: IPv4 Address
* Indicator Type: Malicious Activity
* Confidence Score: 90
* Severity: High
* Status: Active
* Valid Until: One year from creation

---

# Indicator 2 – Malicious Domain

## Observable Type

Domain Name

## Purpose

The domain indicator represents a suspicious domain that can be correlated with DNS activity, web traffic, and other security telemetry collected by Microsoft Sentinel.

## Configuration

* Object Type: Indicator
* Observable: Domain Name
* Indicator Type: Malicious Activity
* Confidence Score: 90
* Severity: High
* Status: Active
* Valid Until: One year from creation

---

# Indicator 3 – Malicious SHA-256 File Hash

## Observable Type

SHA-256 File Hash

## Purpose

The SHA-256 indicator represents a known malicious file hash that can be matched against endpoint telemetry and malware detections.

## Configuration

* Object Type: Indicator
* Observable: SHA-256
* Indicator Type: Malicious Activity
* Confidence Score: 90
* Severity: High
* Status: Active
* Valid Until: One year from creation

---

## Summary

The implementation successfully demonstrated manual creation of three different IOC types within Microsoft Sentinel Threat Intelligence.

The created indicators provide a foundation for:

* Threat Detection
* Threat Hunting
* Security Investigations
* Incident Response
* IOC Correlation
* Threat Intelligence Management

The indicators are now available within the Microsoft Sentinel Threat Intelligence repository and can be incorporated into future analytics rules, automation workflows, and investigation activities.

