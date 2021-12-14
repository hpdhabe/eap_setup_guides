# Steps to configure an EAP-FAST server

Configuring the hostapd server to enable EAP-FAST authentication method is not as straight forward as other enterprise authentication methods because of it's arcane and esoteric nature. Hope this document sheds some light and help you with configuring the server relatively easily. Cheers. :smile:

1. lnstall below mentioned packages/libraries

    ```bash
    apt install pkg-config
    apt install libnl-3-dev
    apt install libssl-dev
    apt install libnl-genl-3-dev
    ```

2. Download the hostapd:

    ```bash
    wget https://w1.fi/releases/hostapd-2.7.tar.gz
    tar xzvfhostapd-2.7.tar.gz
    cd hostapd-2.7/hostapd
    ```

3. In the `defconfig` file, enable the config `CONFIG_EAP_FAST=y`
4. Copy the defconfig and make the library

    ```bash
    cp defconfig .config
    make
    ```

5. Genrate the DH parameter using the following command:

    ```bash
    openssl dhparam -out hostapd.dh 2048
    ```

Depending on the potato-ness of your computer, it might take anywhere between 10 and 30 minutes to complete the make. Once the library is made, use the attached file `hostapd_eap_fast.conf` and start the server.
