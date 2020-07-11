# Ansible Role: `jd_cmd`

Installs or uninstalls [jd-cmd](https://github.com/kwart/jd-cmd) - a simple
command line wrapper around JD Core Java Decompiler project. Creates or removes
a wrapper `jd-cli` to start the program.

## Requirements

- A recent version of Ansible. Tested on 2.9. It might work on previous versions.
- Fedora 31. It might work on other versions.
- Access to an archive of jd-cmd release. Either by URL to download or
  path to a file.

## Role Variables

All variables which can be overridden are stored in
[defaults/main.yml](defaults/main.yml) file and listed in a table bellow as
well.

| Name                        | Default Value | Description  |
| --------------------------- | ------------- | ------------ |
| `jd_cmd_archive_src`        | ""            | Path to an release archive of jd-cmd on a control host or URL to download the archive from. |
| `jd_cmd_state`              | present       | By default installs the program. Set to "absent" to uninstall. |
| `jd_cmd_top_dest_name`      | jd-cmd        | Base name of installation directory. |
| `jd_cmd_install_parent_dir` | /opt          | Parent directory in which program will be installed. See also `jd_cmd_top_dest_name`. |
| `jd_cmd_force_remove`       | no            | If set to "yes", contents of installation directory is not compared against contents of `jd_cmd_archive_src` when uninstall, upgrade or downgrade. |

`jd_cmd_archive_src` must be overriden from its default value.

## Example Playbook

### Install

To install the program, define path to a jd-cmd release archive from the
internet:

```yaml
- hosts: all
  roles:
    - role: scrool.jd_cmd
      vars:
        jd_cmd_archive_src: https://github.com/kwart/jd-cmd/releases/download/jd-cmd-1.1.0.Final/jd-cli-1.1.0.Final-dist.tar.gz
```

### Uninstall

To uninstall, set state variable to "absent":

```yaml
- hosts: all
  roles:
    - role: scrool.jd_cmd
      vars:
        jd_gui_state: absent
```

## License

This project is licensed under MIT License. See [LICENSE](LICENSE) for more
details.

See [jd-cmd](https://github.com/kwart/jd-cmd) for license information.

## Author Information

- [Pavol Babinčák](https://github.com/scrool)
