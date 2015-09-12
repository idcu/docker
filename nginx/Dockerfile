FROM idcu/debian:jessie

ENV NGINX_VERSION 1.9.4-1~jessie

RUN apt-key adv --keyserver hkp://pgp.mit.edu:80 --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62 \
	&& apt-key adv --keyserver hkp://pgp.mit.edu:80 --refresh-keys \
	&& echo 'deb http://nginx.org/packages/mainline/debian/ jessie nginx\n \
		deb-src http://nginx.org/packages/mainline/debian/ jessie nginx' > /etc/apt/sources.list.d/nginx.list \
	&& apt-get update && apt-get install -y ca-certificates nginx=${NGINX_VERSION} && rm -rf /var/lib/apt/lists/* \
    && nginx -c /etc/nginx/nginx.conf \
	&& ln -sf /dev/stdout /var/log/nginx/access.log \
	&& ln -sf /dev/stderr /var/log/nginx/error.log

VOLUME ["/var/cache/nginx", "/app"]

WORKDIR /app

EXPOSE 80 443

CMD ["nginx", "-g", "daemon off;"]