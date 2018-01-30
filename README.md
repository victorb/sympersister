# sympersister
Tiny local service for making sure symlinks always works

## Usage

put in systemd somewhere, call `sumpersister`

Have a config file in `$HOME/.sumpersister/config.json`

```
{
  "/home/user/.zshrc": "/keybase/diggan/private/.zshrc"
}
```

With that config, a symlink will be created to point the value to the key. So when the value changes, key gets updated.

However, once every minute or so, sympersister will copy value to $CACHE so in reality, the symlink is actually pointing to the cache location instead. So if value is not online (like keybase disconnected or you're offline), the symlink will still work. When you get online again, the symlink will point directly to key and work normally again
