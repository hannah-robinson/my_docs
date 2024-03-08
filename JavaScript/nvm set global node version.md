```bash
nvm alias default 20.11.0
```

If it gives this error
```bash
! WARNING: Version '20.11.0' does not exist.
default -> v20.11.0 (-> N/A)
```

Then run this command first
```bash
nvm install 20.11.0
nvm alias default 20.11.0
```
