<!--
  Licensed to the Apache Software Foundation (ASF) under one or more
  contributor license agreements.  See the NOTICE file distributed with
  this work for additional information regarding copyright ownership.
  The ASF licenses this file to You under the Apache License, Version 2.0
  (the "License"); you may not use this file except in compliance with
  the License.  You may obtain a copy of the License at
      http://www.apache.org/licenses/LICENSE-2.0
  Unless required by applicable law or agreed to in writing, software
  distributed under the License is distributed on an "AS IS" BASIS,
  WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
  See the License for the specific language governing permissions and
  limitations under the License.
-->

# SiteToSiteBulletinReportingTask

The Site-to-Site Bulletin Reporting Task allows the user to publish Bulletin events using the Site To Site protocol.
Note: only up to 5 bulletins are stored per component and up to 10 bulletins at controller level for a duration of up to
5 minutes. If this reporting task is not scheduled frequently enough some bulletins may not be sent.

## Record writer

The user can define a Record Writer and directly specify the output format and data with the assumption that the input
schema is the following:

```json
{
  "type": "record",
  "name": "bulletins",
  "namespace": "bulletins",
  "fields": [
    {
      "name": "objectId",
      "type": "string"
    },
    {
      "name": "platform",
      "type": "string"
    },
    {
      "name": "bulletinId",
      "type": "long"
    },
    {
      "name": "bulletinCategory",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinGroupId",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinGroupName",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinGroupPath",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinLevel",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinMessage",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinNodeAddress",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinNodeId",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinSourceId",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinSourceName",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinSourceType",
      "type": [
        "string",
        "null"
      ]
    },
    {
      "name": "bulletinTimestamp",
      "type": [
        "string",
        "null"
      ],
      "doc": "Format: yyyy-MM-dd'T'HH:mm:ss.SSS'Z'"
    },
    {
      "name": "bulletinFlowFileUuid",
      "type": [
        "string",
        "null"
      ]
    }
  ]
}
```