ansible-anydeploy
=========

[![Build Status](https://travis-ci.org/ernestas-poskus/ansible-anydeploy.svg?branch=master)](https://travis-ci.org/ernestas-poskus/ansible-anydeploy)
[![BSD License](http://img.shields.io/badge/license-BSD-blue.svg)](http://opensource.org/licenses/BSD-3-Clause)

Deploy any file, directory or archive to specified deploy folder.
 * 1. Define local commands to execute before deployment
 * 2. Specify files to deploy
 * 3. Define files to extract if applicable

Requirements
------------

None.

Role Variables
--------------

```yaml
deploy_dir: /opt/anydeploy
deploy_user: "{{ansible_user_id}}"
deploy_user_group: "{{ansible_user_id}}"
deploy_dir_mode: 0755
local_commands: []
files_to_transfer: []
files_to_unarchive: []
foreign_commands: []
```

Dependencies
------------

None.

Example Playbook
----------------

```yaml
---
- hosts: localhost
  sudo: yes
  roles:
    - role: ansible-anydeploy
      deploy_dir: ~/tested
      local_commands:
        - touch /tmp/file1
        - touch /tmp/file2
        - tar -czf /tmp/wow.tgz -C /tmp file1 file2
      files_to_transfer:
        - /tmp/wow.tgz
      files_to_unarchive:
        - wow.tgz
      foreign_commands:
        - touch /tmp/self


```

License
-------

Copyright (c) 2016, Ernestas Poskus
All rights reserved.

Redistribution and use in source and binary forms, with or without
modification, are permitted provided that the following conditions are met:

* Redistributions of source code must retain the above copyright notice, this
  list of conditions and the following disclaimer.

* Redistributions in binary form must reproduce the above copyright notice,
  this list of conditions and the following disclaimer in the documentation
  and/or other materials provided with the distribution.

* Neither the name of ansible-anydeploy nor the names of its
  contributors may be used to endorse or promote products derived from
  this software without specific prior written permission.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE
IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE
FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL
DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR
SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

Author Information
------------------

Twitter: @ernestas_poskus
