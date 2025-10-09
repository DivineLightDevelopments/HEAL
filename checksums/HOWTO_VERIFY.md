macOS:  shasum -a 256 <file> | awk '{print $1}'
Linux:  sha256sum <file>       | awk '{print $1}'
