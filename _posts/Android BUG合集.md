# Android BUG合集

1. only DEFLATED entries can have EXT descriptor
2. archive is not a ZIP archive

原因： jar不是标准的zip，替换标准jar，或者解压后用标准zip压缩
