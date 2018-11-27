FROM mysql:5.7

RUN ln -sf /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
RUN echo 'Asia/Shanghai' >/etc/timezone

COPY my.cnf /etc/mysql/

EXPOSE 3306

CMD ["mysqld"]
