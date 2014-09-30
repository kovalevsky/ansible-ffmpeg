# Ansible Role for FFmpeg

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
      - libass-dev
      - libfreetype6-dev
      - libgpac-dev
      - libsdl1.2-dev
      - libtheora-dev
      - libtool
      - libva-dev
      - libvdpau-dev
      - libvorbis-dev
      - libx11-dev
      - libxext-dev
      - libxfixes-dev
      - texi2html
      - zlib1g-dev
      - libmp3lame-dev

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
