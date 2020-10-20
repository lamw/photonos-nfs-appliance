# Reference for building PhotonOS NFS Virtual Appliance (OVA) using Packer

## Requirements

* MacOS or Linux Desktop
* vCenter Server or Standalone ESXi host 6.x or greater
* [VMware OVFTool 4.4.1 (x86)](https://my.vmware.com/group/vmware/downloads/details?downloadGroup=OVFTOOL441&productId=974)
* [Packer 1.6.4+ (x86)](https://www.packer.io/intro/getting-started/install.html)



Step 1 - Clone the git repository

```
git clone https://github.com/lamw/photonos-appliance.git
```

Step 2 - Edit the `photon-builder.json` file to configure the vSphere endpoint for building the PhotonOS appliance

```
{
  "builder_host": "192.168.30.10",
  "builder_host_username": "root",
  "builder_host_password": "VMware1!",
  "builder_host_datastore": "vsanDatastore",
  "builder_host_portgroup": "VM Network"
}
```

**Note:** If you need to change the initial root password on the PhotonOS appliance, take a look at `photon-version.json` and `http/photon-kickstart.json`. When the OVA is produced, there is no default password, so this does not really matter other than for debugging purposes.

Step 3 - Start the build by running the build script which simply calls Packer and the respective build files

```
./build.sh
````

## Try it out

Pre-built [PhotonOS NFS Virtual Appliance OVA](https://download3.vmware.com/software/vmw-tools/photonos-demo/PhotonOS_NFS_Appliance_0.1.0.ova) sample
