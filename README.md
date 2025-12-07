# Ansible Role: FFmpeg

Installs FFmpeg on Ubuntu/Debian systems. Supports both system packages (fast) and compilation from source (full control).

Based on the official FFmpeg [compilation guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

## Requirements

- Ansible 2.10+
- Ubuntu 20.04+ or Debian 11+

## Installation

```bash
ansible-galaxy install kovalevsky.ffmpeg
```

Or add to `requirements.yml`:

```yaml
roles:
  - name: kovalevsky.ffmpeg
    src: https://github.com/kovalevsky/ansible-ffmpeg
```

## Role Variables

### Basic Configuration

```yaml
# Action: install, uninstall, or update
ffmpeg_role_action: install

# Use system packages (fast) or compile from source
ffmpeg_compile_codecs: false

# Remove apt dependencies on uninstall
ffmpeg_remove_deps: false
```

### Directory Configuration

```yaml
ffmpeg_root_dir: "/home/{{ ansible_user }}"
ffmpeg_build_dir: "{{ ffmpeg_root_dir }}/ffmpeg_build"
ffmpeg_source_dir: "{{ ffmpeg_root_dir }}/ffmpeg_sources"
ffmpeg_bin_dir: "{{ ffmpeg_root_dir }}/bin"
```

### Compilation Options

When `ffmpeg_compile_codecs: true`, FFmpeg is compiled with these libraries:
- x264 (H.264 encoder)
- x265 (HEVC encoder)
- fdk-aac (AAC encoder)
- opus (Opus codec)
- libvpx (VP8/VP9)

## Example Playbook

### Quick install (system packages)

```yaml
- hosts: servers
  roles:
    - role: kovalevsky.ffmpeg
```

### Compile from source

```yaml
- hosts: servers
  roles:
    - role: kovalevsky.ffmpeg
      ffmpeg_compile_codecs: true
```

### Uninstall

```yaml
- hosts: servers
  roles:
    - role: kovalevsky.ffmpeg
      ffmpeg_role_action: uninstall
      ffmpeg_remove_deps: true
```

## Testing

This role uses Molecule for testing:

```bash
# Install dependencies
pip install molecule molecule-docker ansible-lint

# Run tests
molecule test
```

## Supported Platforms

- Ubuntu 20.04 (Focal)
- Ubuntu 22.04 (Jammy)
- Ubuntu 24.04 (Noble)
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)

## License

BSD-3-Clause

## Author

[Sergey Kovalevsky](https://github.com/kovalevsky) / HttpLab
