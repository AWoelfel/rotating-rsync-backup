# rotating-rsync-backup
A rsync based backup script with rotation


`./rotating-rsync-backup <SOURCE> <TARGET> <KEEP_NUM> <TODAY>`
1. will copy all contents of `<SOURCE>`  
2. ensures that there are only `<KEEP_NUM>` copies stored in `<TARGET>`

A run of the script will create
- `<TARGET>/<TODAY>/backup/` containing the contents of `<SOURCE>`
- `<TARGET>/<TODAY>/rsync.log` containing the log of `rsync`
- `<TARGET>/<TODAY>/backup.log` containing additional information of the backup run
  - the command which was executed
  - a warning if the target directory already exists
  - a list of directories which where dropped because the `<KEEP_NUM>` threshold was reached

## Examples
- to do a daily backup with one week retention time do `./rotating-rsync-backup <SOURCE> <TARGET> 7 "$(date +%Y-%m-%d)"`
- to do a daily backup with one month of retention time do `./rotating-rsync-backup <SOURCE> <TARGET> 30 "$(date +%Y-%m-%d)"`
- to do a monthly backup with one year retention time do `./rotating-rsync-backup <SOURCE> <TARGET> 12 "$(date +%Y-%m)"`
