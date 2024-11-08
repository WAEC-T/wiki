### How to setup presistant storage for the docker images in the Rasberry


### Step-by-Step Configuration for Persistent Storage on Alpine Linux

1. **Partition Setup**:
    - You already have two partitions:
        - **`RPI_BOOT`**: 15.9 GB (FAT32) for boot files.
        - **Second Partition**: 15.9 GB (FAT32, should be changed to ext4 for persistent storage).
    - The second partition needs to be **converted to `ext4`** for better compatibility and persistence.
2. **Format the Second Partition**:
    - Connect the SD card to your Raspberry Pi or another system that can modify partitions.
    - Format the second partition (`/dev/mmcblk0p2`) as **ext4**:
        
        ```
        sh
        Code kopieren
        mkfs.ext4 /dev/mmcblk0p2
        
        ```
        
3. **Mount the Persistent Storage**:
    - Create a directory to mount the persistent storage:
        
        ```
        sh
        Code kopieren
        mkdir -p /media/persist
        
        ```
        
    - Mount the partition:
        
        ```
        sh
        Code kopieren
        mount /dev/mmcblk0p2 /media/persist
        
        ```
        
    - To make sure it is mounted on every boot, add an entry to **`/etc/fstab`**:
        
        ```
        sh
        Code kopieren
        /dev/mmcblk0p2 /media/persist ext4 rw,relatime 0 1
        
        ```
        
4. **Configure Docker to Use Persistent Storage**:
    - By default, Docker stores data under `/var/lib/docker`, which is currently being loaded into **RAM**.
    - Move Docker's data directory to the persistent storage:
        
        ```
        sh
        Code kopieren
        mkdir -p /media/persist/docker
        
        ```
        
    - Edit Docker’s **configuration** file to point to the new directory:
        - Create or edit the file **`/etc/docker/daemon.json`**:
            
            ```json
            json
            Code kopieren
            {
              "data-root": "/media/persist/docker"
            }
            
            ```
            
    - Restart Docker to apply the changes:
        
        ```
        sh
        Code kopieren
        service docker restart
        
        ```
        