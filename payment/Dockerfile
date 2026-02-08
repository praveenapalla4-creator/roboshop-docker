FROM python:3.9
EXPOSE 8080
WORKDIR /opt/server/
COPY *.py .
COPY  requirements.txt .
RUN pip3 install -r requirements.txt
ENV CART_PORT="8080" \
    USER_HOST="cart" \
    USER_PORT="8080" \
    AMQP_HOST ="rabbitmq" \
    AMQP_USER="roboshop"\
    AMQP_PASS="roboshop123"

CMD ["uwsgi"," --ini", "payment.ini"]
 


cd /app 
pip3 install -r requirements.txt

CART_HOST=<CART-SERVER-IPADDRESS>
Environment=CART_PORT=8080
Environment=USER_HOST=<USER-SERVER-IPADDRESS>
Environment=USER_PORT=8080
Environment=AMQP_HOST=<RABBITMQ-SERVER-IPADDRESS>
=AMQP_USER=roboshop
Environment=AMQP_PASS=roboshop123