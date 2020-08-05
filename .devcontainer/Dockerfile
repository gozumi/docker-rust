FROM ubuntu:focal

RUN apt-get update && apt-get install -y locales && rm -rf /var/lib/apt/lists/* \
    && localedef -i en_US -c -f UTF-8 -A /usr/share/locale/locale.alias en_US.UTF-8
ENV LANG en_US.utf8

RUN apt-get update && \
    apt-get upgrade -y && \
    apt-get install -y git
    
RUN apt-get install -y zsh curl build-essential
RUN sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
RUN sed -i -e 's/robbyrussell/agnoster/g' ~/.zshrc
RUN chsh -s $(which zsh)
RUN curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh -s -- -y
RUN sed -i -e '$aexport PATH=$HOME/.cargo/bin:$PATH' ~/.zshrc
