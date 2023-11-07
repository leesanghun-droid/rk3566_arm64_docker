## RK3566 BASE ARM64 DOCKER INSTALL

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

sudo apt install fuse-overlayfs</br>

sudo apt install \</br>
apt-transport-https \</br>
ca-certificates \</br>
curl \</br>
gnupg2 \</br>
software-properties-common</br>

curl -fsSL https://download.docker.com/linux/debian/gpg | sudo apt-key add -</br>
sudo apt-key fingerprint 0EBFCD88</br>

sudo add-apt-repository \</br>
"deb [arch=arm64] https://download.docker.com/linux/debian \</br>
$(lsb_release -cs) \</br>
stable"</br>

sudo apt-get update</br>

sudo apt-get install docker-ce docker-ce-cli containerd.io</br>

sudo docker run hello-world</br>
