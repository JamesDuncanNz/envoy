FROM mcr.microsoft.com/devcontainers/universal:2

#ADD OBS REPO
RUN echo 'deb http://download.opensuse.org/repositories/shells:/zsh-users:/zsh-syntax-highlighting/xUbuntu_22.04/ /' | sudo tee /etc/apt/sources.list.d/shells:zsh-users:zsh-syntax-highlighting.list && curl -fsSL https://download.opensuse.org/repositories/shells:zsh-users:zsh-syntax-highlighting/xUbuntu_22.04/Release.key | gpg --dearmor | sudo tee /etc/apt/trusted.gpg.d/shells_zsh-users_zsh-syntax-highlighting.gpg > /dev/null
# install the tooks i wish to use
RUN apt-get update && \
  apt-get install -y sudo \
#  curl \
#  git-core \
#  gnupg \
#  linuxbrew-wrapper \
#  locales \
  zsh \
  zsh-syntax-highlighting
#  wget \
#  fonts-powerline \
  # set up locale
#  && locale-gen en_US.UTF-8

# Set the default shell to bash rather than sh
ENV SHELL /bin/zsh

 # run the installation script  
RUN wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh || true

# install powerlevel10k
RUN git clone --depth=1 https://github.com/romkatv/powerlevel10k.git /home/codespace/.oh-my-zsh/custom/themes/powerlevel10k

ADD .zshrc /home/codespace/.zshrc
ADD .p10k.zsh /home/codespace/.p10k.zsh

# TODO
# Install Buildifer
RUN wget https://github.com/bazelbuild/buildtools/releases/download/6.1.0/buildifier-linux-amd64 && chmod +x ./buildifier-linux-amd64 && mv ./buildifier-linux-amd64 /bin/buildifier
# Install Buildozer
RUN wget https://github.com/bazelbuild/buildtools/releases/download/6.1.0/buildozer-linux-amd64 && chmod +x ./buildozer-linux-amd64 && mv ./buildozer-linux-amd64 /bin/buildozer

