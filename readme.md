## RK3566 BASE ARM64 DOCKER INSTALL

0. 의존성 확인하기 ( 매우중요 )
cd kernel</br>
check-config.sh .config </br>

참고 ref . https://jundolssite.wordpress.com/tag/armlinux/

1. 리눅스 커널 boot.img 교체</br>

==> kernel/arch/arm64/configs/rockchip_linux_defconfig</br>
==> menuconfig 를 사용해서 netfilter 관련 모듈 하나도 안뺴고 전부 y로 셋팅

2. 업로드</br>

3. 리눅스 부팅후</br>
구글 네임서버 등록</br>
sudo chmod 777 /etc/resolv.conf; sudo sed "18 i\nameserver 8.8.8.8\\r\\nnameserver 8.8.4.4" /etc/resolv.conf >resolv_copy.conf; sudo rm /etc/resolv.conf; sudo mv ./resolv_copy.conf /etc/resolv.conf</br>

4. 도커 설치

데비안 기본설치</br>
참조 : https://www.hostwinds.kr/tutorials/install-docker-debian-based-operating-system</br>

sudo apt update</br>

sudo apt install \
fuse-overlayfs \
apt-transport-https \
ca-certificates \
curl \
gnupg2 \
software-properties-common</br>

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -</br>

sudo add-apt-repository \
"deb [arch=arm64] https://download.docker.com/linux/debian \
$(lsb_release -cs) \
stable"

sudo apt-get update</br>

sudo apt-get install docker-ce docker-ce-cli containerd.io</br>

sudo docker run hello-world</br>






arm에서 amd64 실행하는 참고내용

sudo fdisk -l

sudo mount -t vfat /dev/sdb1 /mnt/usb_memory

sudo apt install qemu-*-static

sudo /usr/bin/qemu-x86_64-static rkImageMaker -unpack ./update_userdebug_2023.10.18.11.29.img output || pause

sudo /usr/bin/qemu-x86_64-static afptool -unpack output/firmware.img output || pause