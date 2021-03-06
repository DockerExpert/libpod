% podman(1) podman-save - Simple tool to save an image to an archive
% Urvashi Mohnani
# podman-save "1" "July 2017" "podman"

## NAME
podman\-save - Save an image to docker-archive or oci-archive

## SYNOPSIS
**podman save**
**NAME[:TAG]**
[**--quiet**|**-q**]
[**--format**]
[**--output**|**-o**]
[**--help**|**-h**]

## DESCRIPTION
**podman save** saves an image to either **docker-archive**, **oci-archive**, **oci-dir** (directory
with oci manifest type), or **docker-dir** (directory with v2s2 manifest type) on the local machine,
default is **docker-archive**. **podman save** writes to STDOUT by default and can be redirected to a
file using the **output** flag. The **quiet** flag suppresses the output when set.

**podman [GLOBAL OPTIONS]**

**podman save [GLOBAL OPTIONS]**

**podman save [OPTIONS] NAME[:TAG]**

## OPTIONS

**--compress**

Compress tarball image layers when pushing to a directory using the 'dir' transport. (default is same compression type, compressed or uncompressed, as source)
Note: This flag can only be set when using the **dir** transport i.e --format=oci-dir or --format-docker-dir

**--output, -o**
Write to a file, default is STDOUT

**--format**
Save image to **oci-archive**, **oci-dir** (directory with oci manifest type), or **docker-dir** (directory with v2s2 manifest type)
```
--format oci-archive
--format oci-dir
--format docker-dir
```

**--quiet, -q**
Suppress the output

## EXAMPLES

```
# podman save --quiet -o alpine.tar alpine:2.6
```

```
# podman save > alpine-all.tar alpine
```

```
# podman save -o oci-alpine.tar --format oci-archive alpine
```

```
# podman save --compress --format oci-dir -o alp-dir alpine
Getting image source signatures
Copying blob sha256:2fdfe1cd78c20d05774f0919be19bc1a3e4729bce219968e4188e7e0f1af679d
 1.97 MB / 1.97 MB [========================================================] 0s
Copying config sha256:501d1a8f0487e93128df34ea349795bc324d5e0c0d5112e08386a9dfaff620be
 584 B / 584 B [============================================================] 0s
Writing manifest to image destination
Storing signatures
```

```
# podman save --format docker-dir -o ubuntu-dir ubuntu
Getting image source signatures
Copying blob sha256:660c48dd555dcbfdfe19c80a30f557ac57a15f595250e67bfad1e5663c1725bb
 45.55 MB / 45.55 MB [======================================================] 8s
Copying blob sha256:4c7380416e7816a5ab1f840482c9c3ca8de58c6f3ee7f95e55ad299abbfe599f
 846 B / 846 B [============================================================] 0s
Copying blob sha256:421e436b5f80d876128b74139531693be9b4e59e4f1081c9a3c379c95094e375
 620 B / 620 B [============================================================] 0s
Copying blob sha256:e4ce6c3651b3a090bb43688f512f687ea6e3e533132bcbc4a83fb97e7046cea3
 849 B / 849 B [============================================================] 0s
Copying blob sha256:be588e74bd348ce48bb7161350f4b9d783c331f37a853a80b0b4abc0a33c569e
 169 B / 169 B [============================================================] 0s
Copying config sha256:20c44cd7596ff4807aef84273c99588d22749e2a7e15a7545ac96347baa65eda
 3.53 KB / 3.53 KB [========================================================] 0s
Writing manifest to image destination
Storing signatures
```

## SEE ALSO
podman(1), podman-load(1), crio(8)

## HISTORY
July 2017, Originally compiled by Urvashi Mohnani <umohnani@redhat.com>
