# ===========================
# stage 1: Builder(Alpine)
# ==========================

FROM python:3..9.25-alpine3.21 AS builder
WORKDIR /opt/server/
#build deps fro uwsgi & friends
RUN apk add --no-cache \
    build-base \
    linux-headers\
    pcre-dev
#onlu requirements first for caching
COPY requirements.txt .
# COPY payment.ini *.py requirements.txt .
RUN pip3 install --prefix=/install -r requirements.txt

# ===========================
# stage 1: Runtime (Alpine)
# ==========================
FROM python:3.9.25-alpine3.21
EXPOSE 8080
WORKDIR /opt/server/
# Runtime deps only
RUN apk add --no-cache pcre
#createnon-root user
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop 
#copy installed pavakges from builder
COPY --from=builder /install /usr/local
# copy app files
COPY --chown=roboshop:roboshop payment.ini *.py requirements.txt .
ENV CART_PORT="8080" \
    USER_HOST="cart" \
    USER_PORT="8080" \
    AMQP_HOST="rabbitmq" \
    AMQP_USER="roboshop" \
    AMQP_PASS="roboshop123"
USER roboshop
CMD ["uwsgi","--ini", "payment.ini"]
 





# FROM python:3.9
# EXPOSE 8080
# WORKDIR /opt/server/
# COPY payment.ini .
# COPY *.py .
# COPY  requirements.txt .
# RUN pip3 install -r requirements.txt
# ENV CART_PORT="8080" \
#     USER_HOST="cart" \
#     USER_PORT="8080" \
#     AMQP_HOST="rabbitmq" \
#     AMQP_USER="roboshop"\
#     AMQP_PASS="roboshop123"

# CMD ["uwsgi","--ini", "payment.ini"]
 

