---
title: Apache APISIX Helm Chart
---

<!--
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
-->

# Apache APISIX Helm Chart

## Dependencies

Update the dependency chart

```shell
$ helm repo add bitnami https://charts.bitnami.com/bitnami
$ helm dependency update .
```

## Install

To install the chart with release name `apisix`:

```shell
$ helm install apisix . -n default
```

## Uninstall

To uninstall/delete the `apisix` release:

```shell
helm uninstall apisix . -n default
```

## FAQ

1. How to install APISIX only?

The Charts will install etcd 3.4.14 by default. If you want to install Apache APISIX only, please set `etcd.enabled=false` and set `etcd.host={http://your_etcd_address:2379}`.

Please use the FQDN address or the IP of the etcd.

```shell
# if etcd export by kubernetes service need spell fully qualified name
$ helm install apisix . -n default \
    --set etcd.enabled=false \
    --set etcd.host={http://etcd_node_1:2379\,http://etcd_node_2:2379}
```

2. Why get 403 when I access Apache APISIX admin api?

We can define `allow.ipList` in CIDR.

```shell
$ helm install apisix . -n default \
    --set allow.ipList="10.22.100.12/8" \
    --set allow.ipList="172.0.0.0/24"
```

If you want to allow all IPs for a quick test, just set `allow.ipList=""`

```shell
$ helm install apisix . -n default \
    --set allow.ipList=""
```

## Seeking help

- Mailing List: Mail to dev-subscribe@apisix.apache.org, follow the reply to subscribe the mailing list.
- QQ Group - 578997126, 552030619
- [Slack Workspace](http://s.apache.org/slack-invite) - join `#apisix` on our Slack to meet the team and ask questions
- ![Twitter Follow](https://img.shields.io/twitter/follow/ApacheAPISIX?style=social) - follow and interact with us using hashtag `#ApacheAPISIX`
- [bilibili video](https://space.bilibili.com/551921247)
