# Mount an Azure blob storage on Linux using NFSv3 protocol

## On your Linux machine

1. Install the AZNFS Mount Helper package ([See more details here]).(https://learn.microsoft.com/en-us/azure/storage/blobs/network-file-system-protocol-support-how-to#step-5-install-the-aznfs-mount-helper-package)

```console
wget -O - -q https://github.com/Azure/AZNFS-mount/releases/latest/download/aznfs_install.sh | sudo bash
```
2. Create a directory as a mounting point
```console
sudo mkdir -p /mnt/myblobnfs
```
3. To mount the directory, modify the mount command template and run the command
```console
sudo mount -t aznfs -o sec=sys,vers=3,nolock,proto=tcp <storage-account-name>.blob.core.windows.net:/<storage-account-name>/<container-name> <mounting-directory>
```
4. In my case, the command reads:
```console
sudo mount -t aznfs -o sec=sys,vers=3,nolock,proto=tcp jarunanpblobstorage.blob.core.windows.net:/jarunanpblobstorage/myblob /mnt/myblobnfs
```
To test the mounted directory, store a file in the mounted directory and see if it appears in the container on the portal
```console
cd /mnt/myblobnfs
mkdir test
echo "hello world" > test/blob.txt
```
To unmount the directory
```console
sudo umount -l myblobnfs
```
**References**  
https://unlimited.ethz.ch/display/itkb/Mount+an+Azure+blob+storage+on+Linux+using+NFSv3+protocol
