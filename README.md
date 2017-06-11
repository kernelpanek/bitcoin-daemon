Bitcoin Daemon Role
=========

A simple role for installing a Bitcoin daemon via source compilation. 

Requirements
------------

A Debian-based host

Role Variables
--------------

| Variable | Description |
--------------------------
| bitcoin_host_type | A compilation target tuple. Useful for targeting compilation on hardware other than `x86_64-unknown-linux-gnu`. |
| bitcoin_repo_url | The Git-accessible path to the Bitcoin source code. | 
| bitcoin_repo_checkout | The branch or commit to checkout. | 
| bitcoin_ccache_size | The cache size. e.g. `100M` |
| bitcoin_checksums | A list of SHA256 checksums to validate the compiled binaries. The default values will require change if the `bitcoin_repo_checkout` variable is changed from its default value. |
| bitcoin_conf | A list of configuration lines (key=value pairs) |
| bitcoin_installdir | The base directory to install Bitcoin. |
| bitcoin_bindir | The `bin` directory location of Bitcoin. |
| bitcoin_libdir | The `lib` directory location of Bitcoin. |
| bitcoin_configure_options | Configuration switches to set before compiling the distribution directory. |
| bitcoin_host_configure_options | Configuration switches to set before compiling the installation. |
| compilation_packages | A list of package names to install prior to compilation. |

Molecule
--------

This role can be tested using Molecule.

 Install ...

```bash
pip install molecule
```

 Run ...

```bash
molecule converge
```

Dependencies
------------

None

Example Playbook
----------------

```yaml
- hosts: servers
  roles:
     - { role: bitcoin-daemon }
```

Ansible-container
-----------------

To build this role as a docker image, run:

```bash
pip install ansible-container[docker]
ansible-container build
```

Deploy role to Amazon ec2
-------------------------

Run: ...

```bash
ansible-playbook -i "localhost," -c local ec2.yml
```

License
-------

BSD

