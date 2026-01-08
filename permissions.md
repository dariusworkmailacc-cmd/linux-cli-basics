# Permissions

## What I practiced
- Viewing permissions using `ls -l`
- Modifying permissions with `chmod`
- Using numeric permission modes

## Permission basics
- r = read
- w = write
- x = execute

Permissions apply to:
- Owner (user)
- Group
- Others

Example:
-rwxr-xr--

## Numeric permissions
- 600 → owner read/write
- 644 → owner read/write, others read
- 755 → executable directory or script

## Security notes
- 777 grants full access to everyone and is unsafe
- PoLP reduces the attack surface
  
