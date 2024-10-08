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

# HazelcastMapCacheClient

This implementation of distributed map cache is backed by Hazelcast. The Hazelcast connection is provided and maintained
by an instance of HazelcastCacheManager. One HazelcastCacheManager might serve multiple cache clients. This
implementation uses the IMap data structure. The identifier of the Hazelcast IMap will be the same as the value of the
property Hazelcast Cache Name. It is recommended for all HazelcastMapCacheClient instances to use different cache names.

The implementation supports the atomic method family defined in AtomicDistributedMapCacheClient. This is achieved by
maintaining a revision number for every entry. The revision is an 8 byte long integer. It is increased when the entry is
updated. The value is kept during modifications not part of the atomic method family but this is mainly for regular
management of the entries. It is not recommended to work with elements by mixing the two method families.

The convention for all the entries is to reserve the first 8 bytes for the revision. The rest of the content is the
serialized payload.