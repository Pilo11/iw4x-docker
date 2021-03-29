FROM mcr.microsoft.com/dotnet/sdk:3.1

RUN apt-get update -y \
    && apt-get full-upgrade -y \
    && apt-get install unzip \
    && adduser -q --gecos "" --home /iw4x --disabled-password iw4x \
    && mkdir /iw4x/server \
    && mkdir /iw4x/admin \
    && wget -O IW4MAdmin.zip https://github.com/RaidMax/IW4M-Admin/releases/download/2021.03.28.1-prerelease/IW4MAdmin-2021.03.28.1.zip \
    && unzip IW4MAdmin.zip -d /iw4x/admin \
    && rm -f IW4MAdmin.zip

COPY Configuration /iw4x/admin/Configuration
COPY Database /iw4x/admin/Database

RUN chown -R iw4x:iw4x /iw4x

USER iw4x
WORKDIR /iw4x/admin

VOLUME ["/iw4x/server"]

EXPOSE 1624

CMD ["/bin/sh", "-e", "StartIW4MAdmin.sh"]