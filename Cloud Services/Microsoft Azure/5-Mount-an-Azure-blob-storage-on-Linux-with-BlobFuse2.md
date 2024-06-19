# Mount an Azure blob storage on Linux with BlobFuse2

## On your Linux machine
In this tutorial follows How to mount an Azure Blob Storage container on Linux with BlobFuse2, the command were run on Ubuntu 20.04.

1. Configure the Linux package repository for Windows products
```console
sudo wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo apt-get update
sudo apt-get install libfuse3-dev fuse3
```
2. Install BlobFuse2
```console
sudo apt-get install blobfuse2
```
3. Create a temporary directory for small cache
```console
mkdir -p /tmp/blobfuse2_cache
```
4. Download the sample configuration file for BlobFuse2 and use a text editor, e.g., emacs, to edit the file
```console
wget --no-check-certificate --content-disposition https://raw.githubusercontent.com/Azure/azure-storage-fuse/main/sampleFileCacheConfig.yaml
mv sampleFileCacheConfig.yaml config.yaml
emacs config.yaml
```
5. Edit the section file_cache for small files and enter the storage name and access key
```console
...
file_cache:
  path: /tmp/blobfuse2_cache
...
azstorage:
  type: block
  account-name: blobjarunan216121
  account-key: 0YIBktENKRkvDXR4X4GrLKyIqScO99lVZ12345BEBD/K8rxm4N8ED6G957yG0tgs==
  endpoint: https://blobjarunan216121.blob.core.windows.net
  mode: key
  container: content
```
6. Create a directory
```console
sudo mkdir -p /mnt/myblob_blobfuse2
```
7. Mount the directory
```console
sudo blobfuse2 mount /mnt/myblob_blobfuse2 --config-file=./config.yaml
```
8. To test the mounted directory, store a file in the mounted directory and see if it appears in the container on the portal
```console
cd /mnt/myblob_blobfuse2
mkdir test
echo "hello world" > test/blob.txt
```
* [Reference](https://unlimited.ethz.ch/display/itkb/Mount+an+Azure+blob+storage+on+Linux+with+BlobFuse2)
