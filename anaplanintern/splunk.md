---
description: Log data analysis tool
---

# Splunk

## Why Explore Logs Challenge?

Huge number of logs, record so many information. How to do that in real time and analysis in real time

## What Splunk Does?

Real time log --> Logs forward to remote instance in a human readable form --> Do real time analysis (IP traffic, how many users, Regional data, ...) --> Provide real time alert and notifications (CPU performance, IP range, ...) --> Historical data and log store & analysis (last 30 days of log data to be analyzed)

## How Splunk Works?

Distributed System to ensure data availability

#### Forwarders

* Collect data and forward to other splunk instances

#### Indexers

* Log comes in real time and store here, receive logs from forwarders.&#x20;

#### Search Hands/Cluster Members

* Process data and do calculations, give alerts

#### Deployer

* Make sure updates to config and ops are sent to clusters (cluster members form search engine)

#### Cluster Master

* Responsible for: 1. All peers of indexers are up; 2. Manage different search heads and tells them where to go find data and problems

#### Deployment Server

* Similar to Deployer, but do work to forwarders. Update data are sent to the forwarders and are sent out correctly.
