#
# Copyright (c) 2021 Matthew Penner
#
# Permission is hereby granted, free of charge, to any person obtaining a copy
# of this software and associated documentation files (the "Software"), to deal
# in the Software without restriction, including without limitation the rights
# to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
# copies of the Software, and to permit persons to whom the Software is
# furnished to do so, subject to the following conditions:
#
# The above copyright notice and this permission notice shall be included in all
# copies or substantial portions of the Software.
#
# THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
# IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
# FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
# AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
# LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
# OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
# SOFTWARE.
#

############################ WIP

FROM        alpine:3.16

LABEL       author="Michael Hesemann" maintainer="michael@fave.lu"

LABEL       org.opencontainers.image.source="https://github.com/Sauc1ness/yolks/tree/alpine"
LABEL       org.opencontainers.image.licenses=MIT

RUN			adduser --disabled-password --home /home/container container
WORKDIR     /home/container

RUN         apk update && apk add curl tar && \
			rm -rf /var/cache/apk/* && \ 
			curl http://media.steampowered.com/installer/steamcmd_linux.tar.gz --output steamcmd.tar.gz --silent && \
			tar -xvzf steamcmd.tar.gz && rm steamcmd.tar.gz && \
			mv
			

COPY /root/installer/steamcmd.sh /usr/lib/games/steam/
COPY /root/installer/linux32/steamcmd /usr/lib/games/steam/
COPY /usr/games/steamcmd /usr/bin/steamcmd

USER        container
ENV         USER=container HOME=/home/container

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/sh", "/entrypoint.sh" ]