Ansible Module - gsetting
=========================

**Ansible module used to configure modern GNOME applications.**

Installation
------------

1. Download with curl

    ```
    curl -O https://raw.githubusercontent.com/AsavarTzeth/ansible-gsetting/master/gsetting
    ```

2. Clone the repository

    ```
    git clone https://github.com/AsavarTzeth/ansible-gsetting.git
    ```

Requirements
------------

The host must have dbus and gsettings installed.

Examples
--------

    # Double qoute strings to preserve the single qoutes
    - gsetting:
        key: org.gnome.nautilus.preferences.default-folder-viewer
        value: "'list-view'"

    # Get current value of a key without making any changes
    - gsetting:
        key: org.gnome.nautilus.preferences.default-folder-viewer
        state: get

    # Reset key to its default value
    - gsetting:
        key: org.gnome.nautilus.preferences.default-folder-viewer
        state: absent

    # Set the value of a key for different user
    - gsetting:
        key: org.gnome.desktop.wm.preferences.audible-bell
        value: "false"
      become: true
      become_user: "{{ username }}"

    # Set a list type value of a key
    - gsetting:
        key: org.gnome.nautilus.list-view.default-visible-columns
        value: "['name','size','type','date_modified']"

    # Set a null value list
    - gsetting:
        key: org.gnome.desktop.wm.keybindings.panel-main-menu
        value: "@as []"

    # Set a list of tuples
    - gsetting:
        key: org.gnome.desktop.input-sources.sources
        value: "[('xkb','se'),('xkb','us')]"

    # Set a 32 bit integer
    - gsetting:
        key: org.gnome.desktop.interface.scaling-factor
        value: "uint32 2"
