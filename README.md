# How-to-add-docker-image-with-yocto
Adding Docker to a Yocto image involves several steps, including adding the necessary layers, updating the local.conf, and adding Docker to your image.

## Steps
- Lets add the meta-virtulization layer first go to poky ```git clone https://git.yoctoproject.org/meta-virtualization```
- Source the enviroment ``` source oe-init-build-env```
- Add the layer ```bitbake-layers add-layer ../meta-virtualization```
- U would get that error probaply
![Screenshot from 2024-08-07 13-55-46](https://github.com/user-attachments/assets/9d3d211c-026c-4a7a-a28d-105f493499b4)
- This error tells u to add this layer also ```bitbake-layers add-layer ../meta-openembedded/meta-filesystems```
- Then do this again ```bitbake-layers add-layer ../meta-virtualization```
![Screenshot from 2024-08-07 14-00-21](https://github.com/user-attachments/assets/72e1892f-b541-44a2-8344-07ae39397906)
- DONE HERE

## Local.conf File
- Add this 2 lines
```
DISTRO_FEATURES:append = " virtualization"
IMAGE_INSTALL:append = " docker-ce"
```
- DISTRO_FEATURES defines the features and capabilities that are included in the distribution. This can include support for various packages, libraries, or system capabilities.
- IMAGE_INSTALL specifies the list of packages that should be installed in the final image. This directly affects the contents of the image being built.
- For space space use this ``` IMAGE_ROOTFS_SIZE = "2194304"```

![Screenshot from 2024-08-07 14-40-48](https://github.com/user-attachments/assets/6014ec38-83d1-4fbf-a54b-b03826361d8d)
- Bingo docker is working now
## Neuron docker image
- Neuron is an open-source, lightweight IIoT connectivity server that empowers industrial devices with the key IoT connectivity capabilities in the Industry 4.0 era.
- Pull the image ```docker pull emqx/neuron-en```
  ![Screenshot from 2024-08-07 14-43-48](https://github.com/user-attachments/assets/7c253704-eb48-4097-a532-eab38cd3d413)
- Already downloaded
![Screenshot from 2024-08-07 14-44-28](https://github.com/user-attachments/assets/8fb6585a-5960-4a31-aef8-79463bac09cf)
- Run the contanier
![Screenshot from 2024-08-07 14-48-19](https://github.com/user-attachments/assets/276edddf-0fb7-4588-9e51-7f74e3a112e4)
- I lanuched neruon at the rasbperry localhost and port 7000
![Screenshot from 2024-08-07 14-49-12](https://github.com/user-attachments/assets/84d37324-3aee-48bc-9555-387674ddd44b)

- Done !!

 ![Screenshot from 2024-08-07 14-50-36](https://github.com/user-attachments/assets/d3776f34-6722-4321-bee4-082d06c3dd1e)




