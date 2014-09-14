# Ansible Role for FFmpeg

A Role to compile FFmpeg and it's major dependencies from sources and install it all. Supports updating and removing.
Based on official FFmpeg [compilation guide](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu).

## Role Variables

```yaml
ffmpeg_role_action: # ['install'|'updade'|'uninstall'], default: 'install'
ffmpeg_remove_deps: # Remove dependencies installed from apt, default: false
```

## License

BSD