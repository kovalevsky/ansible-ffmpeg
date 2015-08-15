# Ansible Role for FFmpeg

[![Build Status](https://travis-ci.org/kovalevsky/ansible-ffmpeg.svg)](https://travis-ci.org/kovalevsky/ansible-ffmpeg)

A Role to compile FFmpeg and it's major dependencies from sources and install it all. Supports updating and removing.
Based on official FFmpeg [compilation guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

Requirements
------------

none

Role Variables
------------

Defaults is:

    ffmpeg_role_action: 'install'
    ffmpeg_remove_deps: false

    ffmpeg_root_dir: "~{{ ansible_ssh_user }}"

    ffmpeg_build_dir: "{{ ffmpeg_root_dir }}/ffmpeg_build_dir"
    ffmpeg_source_dir: "{{ ffmpeg_root_dir }}/ffmpeg_sources"
    ffmpeg_bin_dir: "{{ ffmpeg_root_dir }}/bin"
    ffmpeg_env:
      PKG_CONFIG_PATH: "{{ ffmpeg_build_dir }}/lib/pkgconfig"

ffmpeg_deps:
  - cmake
  - libass-dev
  - libfreetype6-dev
  - libtheora-dev
  - libtool
  - libvorbis-dev
  - pkg-config 
  - texi2html
  - zlib1g-dev

Description: 

- `ffmpeg_role_action` – install, uninstall or update FFmpeg installed from this role, default: 'install'. 
- `ffmpeg_remove_deps` – Remove dependencies installed from apt, default: false.

Dependencies
------------

none

License
------------

BSD

Author Information
------------------

[Sergey Kovalevsky](http://github.com/kovalevsky)
