FROM amazonlinux:2

# timezone設定
RUN ln -sf /usr/share/zoneinfo/Asia/Tokyo /etc/localtime

RUN yum update -y && amazon-linux-extras install nginx1 -y

COPY ./default.conf /etc/nginx/conf.d/default.conf

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]
