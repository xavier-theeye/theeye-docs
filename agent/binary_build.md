
# Build TheEye Agent (Unix)

### Prerequisites

* EncloseJS with the Key configured
* TheEye-Agent installed and configured
* Git
* npm 3
* Linux

### HOWTO

`cat misc/run_enclose.sh `

```bash

#!/bin/bash

root="$PWD"

cd $root/node_modules/config
npm install hjson toml cson properties

cd $root
enclose -o bin/theeye-agent -l warning core/main.js
```


From theeye-agent's script root path , run the script

`./misc/run_enclose.sh`

The script will generate the binary agent into `bin` directory.
Then copy these node bindings for your platform. those files are generated by npm and placed within `node_modules` directory
at the moment You ran `npm install`.

There are two bindings

* binding.node
* ffi_bindings.node

You will usually found the files in the following path

* ./ref/build/Release/binding.node
* ./ref/build/Release/obj.target/binding.node
* ./ffi/build/Release/ffi_bindings.node
* ./ffi/build/Release/obj.target/ffi_bindings.node


Finally copy the `config` directory within `bin`. The result should be similar as shown bellow:

```bash
@facugon dice (development): ls -la bin
total 29832
drwxrwxr-x 4 facugon facugon 4096 feb 10 09:14 .
drwxrwxr-x 12 facugon facugon 4096 feb 10 11:38 ..
-rwxrwxr-x 1 facugon facugon 43104 feb 10 09:13 binding.node
drwxrwxr-x 2 facugon facugon 4096 feb 10 11:40 config
drwxr-xr-x 2 facugon facugon 4096 feb 10 09:14 downloads
-rwxrwxr-x 1 facugon facugon 80952 feb 10 09:14 ffi_bindings.node
-rwxrwxr-- 1 facugon facugon 30401224 feb 10 09:09 theeye-agent
```

The `downloads` directory is automatically generated by the agent when the scripts are downloaded.
That should be enough. Enjoy!