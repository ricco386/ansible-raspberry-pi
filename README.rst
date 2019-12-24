Ansible role for Raspberry Pi initial setup
===========================================

Ansible role for initial Raspberry Pi setup. Installing a monitor script for Raspberry Pi to find out Raspberry Pi specific parameters values. Role will install raspi-monitor script that can monitor:

* board version
* board revision
* board serialnumber
* firmware version
* cpu voltage
* cpu clock
* cpu memmory
* cpu temperature
* gpu memmory


Role Variables
--------------

Script deployment path:
``rpi_monitor_script: /usr/local/sbin/raspi-monitor``

UserParameters to be checked by Zabbix Agent:
``zabbix_agent_userparameters:
  - {name: "rpi.boardversion", command: "sudo {{ rpi_monitor_script }} boardversion"}
  - {name: "rpi.boardrevision", command: "sudo {{ rpi_monitor_script }} boardrevision"}
  - {name: "rpi.boardserialnumber", command: "sudo {{ rpi_monitor_script }} boardserialnumber"}
  - {name: "rpi.cpuvoltage", command: "sudo {{ rpi_monitor_script }} cpuvoltage"}
  - {name: "rpi.cpuclock", command: "sudo {{ rpi_monitor_script }} cpuclock"}
  - {name: "rpi.cpumem", command: "sudo {{ rpi_monitor_script }} cpumem"}
  - {name: "rpi.firmwareversion", command: "sudo {{ rpi_monitor_script }} firmwareversion"}
  - {name: "rpi.gpumem", command: "sudo {{ rpi_monitor_script }} gpumem"}
  - {name: "rpi.temperature", command: "sudo {{ rpi_monitor_script }} temperature"}``


Dependencies
------------

None


Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters):

.. code-block::

    - hosts: all 
      roles:
        - raspberry-pi-zabbix


Zabbix Template
---------------

Zabbix template ``raspberry-pi-zabbix_template.xml`` is stored in meta directory. You can import this template into your Zabbix in order to start monitoring your Raspberry Pi.

License
-------

MIT


Author Information
------------------

Created by Richard von Kellner (`@RicCo386 <https://twitter.com/ricco386>`_).


Contributing
------------

Contributions are welcome!

Submit issues, ideas or pull requests on GitHub at `https://github.com/ricco386/ansible-raspberry-pi`_.
