FROM ubuntu:latest
RUN apt update && apt install -y openssh-server redis-tools curl gpg
RUN curl -fsSL https://www.postgresql.org/media/keys/ACCC4CF8.asc | gpg --dearmor -o /etc/apt/trusted.gpg.d/postgresql.gpg
RUN sh -c 'echo "deb http://apt.postgresql.org/pub/repos/apt $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list'
RUN apt update && apt install -y postgresql-client-17
RUN mkdir /var/run/sshd
RUN echo 'root:rootpass' | chpasswd
RUN sed -i 's/#PermitRootLogin prohibit-password/PermitRootLogin yes/' /etc/ssh/sshd_config

# Create a user (optional)
# RUN useradd -m user
# RUN echo 'user:password' | chpasswd

EXPOSE 22
CMD ["/usr/sbin/sshd", "-D"]