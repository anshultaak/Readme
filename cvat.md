# Wisy-CVAT Infrastructure Documentation

## Prerequisites

Make sure you have the following tools installed:

- GCloud CLI
- Terraform

## Installation Steps

1. Clone the repository:
    ```
    git clone https://github.com/CloudWerx/wisy-cvat.git
    git checkout dev
    cd wisy-cvat/terraform
    ```

2. Initialize Terraform:
    ```
    terraform init
    ```

3. Plan the infrastructure changes:
    ```
    terraform plan -var-file=dev.tfvars
    ```

4. Apply the Terraform configuration:
    ```
    terraform apply -var-file=dev.tfvars
    ```

## Deployment Steps

### Know About

1. **GCS Fuse**: Learn about persistent volumes with Cloud Storage Fuse CSI Driver.
    [GCS Fuse Documentation](https://cloud.google.com/kubernetes-engine/docs/how-to/persistent-volumes/cloud-storage-fuse-csi-driver)

2. **Provision static GCS buckets**: Guide for provisioning static GCS buckets.
    [Static Bucket Provisioning Guide](https://cloud.google.com/kubernetes-engine/docs/how-to/persistent-volumes/cloud-storage-fuse-csi-driver#provision-static)

3. **Kubernetes Service Account Configuration**:
    Configure Kubernetes service accounts.
    ```
    kubectl annotate serviceaccount default \
        --namespace cvat \
        iam.gke.io/gcp-service-account=cvat-gsa-dev@wisy-cvat.iam.gserviceaccount.com
    ```
4. **setup NFS Server**:
   
### Adding New Desk to VM

Instructions for adding a new desk to VM:
```
sudo mkfs.ext4 /dev/sdb
sudo mkdir /mnt/nfsdisk
sudo mount /dev/sdb /mnt/nfsdisk
sudo nano /etc/fstab
/dev/sdb /mnt/nfsdisk ext4 defaults 0 2
```

### Create NFS Server

Guide for creating an NFS server:
```
sudo apt update
sudo apt install nfs-kernel-server
sudo chown -R nobody:nogroup /mnt/nfsdisk/
sudo chmod -R 777 /mnt/nfsdisk/

## Create folder
sudo mkdir -p /mnt/nfsdisk/cvat/dev
sudo chown -R nobody:nogroup /mnt/nfsdisk/cvat/dev
sudo chmod -R 777 /mnt/nfsdisk/cvat/dev

## Adding new export folder
sudo nano /etc/exports
/mnt/nfsdisk/cvat/dev *(rw,sync,no_subtree_check)
sudo exportfs -a
sudo systemctl restart nfs-kernel-server
```

5. **Setting up Helm**: Instructions for setting up Helm.
    ```
    cd wisy-cvat/kubernetes-manifests/dev
    helm dependency update
    ```

### Running Helm

Commands for running Helm:
```
helm upgrade -n cvat-dev cvat-dev -i ./helm-chart -f helm-chart/values.yaml -f cvat.override-values-dev.yaml
helm uninstall -n cvat-dev cvat-dev
```

### Redis Authentication

Get Redis authentication string:
```
gcloud redis instances get-auth-string wisy-cvat-cache --region=us-east1 --project wisy-cvat
```

### Creating Super User

Exec into backend server pod and run following command:
```
python3 ~/manage.py createsuperuser
wisy-cvat-superadmin
harry.paul@cloudwerx.tech
wisy-cvat-superadmin
```

