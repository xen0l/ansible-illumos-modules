#!/usr/bin/python
# -*- coding: utf-8 -*-

# (c) 2015, Adam Števko <adam.stevko@gmail.com>
#
# This file is part of Ansible
#
# Ansible is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# Ansible is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with Ansible. If not, see <http://www.gnu.org/licenses/>.
#

DOCUMENTATION = '''
---
module: smartos_image_source
short_description: Manage image sources on SmartOS compute nodes.
description:
    - Add/delete image source on SmartOS compute nodes.
version_added: "2.0"
author: Adam Števko (@xen0l)
options:
    url:
        description:
            - URL of the image server.
        required: true
    type:
        description:
            - Specifies the type of the image server.
        required: false
        default: imgapi
        choices: [ "imgapi", "docker", "dsapi" ]
    state:
        description:
            - Set or reset the property value.
        required: true
        default: present
        choices: [ "present", "absent" ]
'''

EXAMPLES = '''
# Add datasets.at image source
smartos_image_source: url=http://datasets.at state=present

# Remove official image source
smartos_image_source: url=https://images.joyent.com state=absent

# Add docker registry as image source
smartos_image_source: url=https://index.docker.io type=docker
'''

SUPPORTED_IMAGE_SOURCE_TYPES = ['imgapi', 'docker', 'dsapi']


class ImageSource(object):

    def __init__(self, module):
        self.module = module

        self.url = module.params['url']
        self.type = module.params['type']
        self.state = module.params['state']

    def image_source_exists(self):
        cmd = [self.module.get_bin_path('imgadm')]

        cmd.append('sources')

        if self.module.check_mode:
            return True

        (rc, out, _) = self.module.run_command(cmd)

        if rc == 0 and self.url in out:
            return True
        else:
            return False

    def add_image_source(self):
        cmd = [self.module.get_bin_path('imgadm')]

        cmd.append('sources')
        cmd.append('-a')
        cmd.append(self.url)
        cmd.append('-t')
        cmd.append(self.type)

        return self.module.run_command(cmd)

    def delete_image_source(self):
        cmd = [self.module.get_bin_path('imgadm')]

        cmd.append('sources')
        cmd.append('-d')
        cmd.append(self.url)

        return self.module.run_command(cmd)


def main():
    module = AnsibleModule(
        argument_spec=dict(
            url=dict(required=True),
            type=dict(required=False, default='imgapi',
                      choices=SUPPORTED_IMAGE_SOURCE_TYPES),
            state=dict(
                default='present', choices=['absent', 'present', 'reset']),
        ),
        supports_check_mode=True
    )

    image_source = ImageSource(module)

    rc = None
    out = ''
    err = ''
    result = {}
    result['state'] = image_source.state
    result['type'] = image_source.type
    result['url'] = image_source.url

    if image_source.state == 'absent':
        if image_source.image_source_exists():
            if module.check_mode:
                module.exit_json(changed=True)

            (rc, out, err) = image_source.delete_image_source()
            if rc != 0:
                module.fail_json(msg='Failed to delete %s' % image_source.url)

    elif image_source.state == 'present':
        if not image_source.image_source_exists():
            if module.check_mode:
                module.exit_json(changed=True)

            (rc, out, err) = image_source.add_image_source()
            if rc != 0:
                module.fail_json(msg='Failed to add %s' % image_source.url)

    if rc is None:
        result['changed'] = False
    else:
        result['changed'] = True

    if out:
        result['stdout'] = out
    if err:
        result['stderr'] = err

    module.exit_json(**result)


from ansible.module_utils.basic import *
main()
