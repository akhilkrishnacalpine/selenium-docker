
FROM siliconvalleyclouldit/seleniumfirefox:latest

USER root

RUN apt-get update -qqy \
  && apt-get -qqy install \
  x11vnc \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

ENV LANGUAGE en_US.UTF-8
ENV LANG en_US.UTF-8
RUN locale-gen en_US.UTF-8 \
  && dpkg-reconfigure --frontend noninteractive locales \
  && apt-get update -qqy \
  && apt-get -qqy --no-install-recommends install \
    language-pack-en \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

RUN apt-get update -qqy \
  && apt-get -qqy --no-install-recommends install \
    fonts-ipafont-gothic \
    xfonts-100dpi \
    xfonts-75dpi \
    xfonts-cyrillic \
    xfonts-scalable \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*


RUN apt-get update -qqy \
  && apt-get -qqy install \
    fluxbox \
  && rm -rf /var/lib/apt/lists/* /var/cache/apt/*

USER seluser


RUN mkdir -p ~/.vnc \
  && x11vnc -storepasswd secret ~/.vnc/passwd

COPY entry_point.sh /opt/bin/entry_point.sh
RUN sudo chmod +x /opt/bin/entry_point.sh

EXPOSE 5900
