# SRv6 End.AM plugin

Endpoint to SR-unaware appliance via masquerading

## Installation

1. **Copy** or **move** this directory as `vpp/src/plugins/srv6-am`

2. **Create** a file `vpp/src/plugins/srv6_am.am` with the following
   content
```make
# Copyright (c) 2016 Cisco Systems, Inc.
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at:
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.

vppplugins_LTLIBRARIES += srv6am_plugin.la

srv6am_plugin_la_SOURCES =			\
	srv6-am/am.c	\
	srv6-am/node.c

noinst_HEADERS += srv6-am/am.h

# vi:syntax=automake
```

3. **Add** to file `vpp/src/plugins/Makefile.am` (~ l. 31):
```make
if ENABLE_SRV6AM_PLUGIN
include srv6_am.am
endif
```

4. **Add** to file `vpp/src/configure.ac` (~ l. 148):
```
PLUGIN_ENABLED(srv6am)
```

