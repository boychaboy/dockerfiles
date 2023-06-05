FROM ubuntu:latest 
MAINTAINER Younghoon Jeong <younghoon.j@navercorp.com>

# General
ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Asia/Seoul
RUN apt-get -y update &&\
 apt-get install -y git wget zsh tzdata vim openssh-server mysql-server mysql-client sudo ufw curl tmux exuberant-ctags
RUN apt install python3 python3-pip -y

# ZSH 
RUN apt-get -y install fonts-powerline
RUN chsh -s /bin/zsh
RUN sh -c "$(wget -O- https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
RUN apt-get -y install fonts-powerline

# ZSH-plugins
RUN git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ~/.oh-my-zsh/custom/plugins/zsh-syntax-highlighting
RUN git clone https://github.com/romkatv/powerlevel10k.git ~/.oh-my-zsh/custom/themes/powerlevel10k
RUN perl -pi -w -e 's/ZSH_THEME=.*/ZSH_THEME="powerlevel10k\/powerlevel10k"/g;' ~/.zshrc
RUN perl -pi -w -e 's/plugins=.*/plugins=(git zsh-syntax-highlighting)/g;' ~/.zshrc

# Time & Location 
RUN sudo apt-get install -y language-pack-en && sudo update-locale

# 설치로 생성된 캐시 파일 삭제
RUN apt-get clean && \
	apt-get autoclean && \
	apt-get autoremove -y && \
	rm -rf /var/lib/cache/* && \
	rm -rf /var/lib/log/*

# EXPOSE : 해당 포트 번호를 외부에 노출한다.
EXPOSE 22 3306
# ssh의 기본 포트 번호는 22, mysql은 3306입니다. 
# 이 포트를 열지 않는다면 우분투가 정상적으로 설치되더라도 외부와 통신을 할 수 없습니다.
CMD ["zsh"]
