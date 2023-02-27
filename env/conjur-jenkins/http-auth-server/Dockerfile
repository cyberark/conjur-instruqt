FROM python:3.9.16-slim-bullseye
COPY ./http_server_auth.py /http_server_auth.py

WORKDIR /
CMD ["python","-m","http_server_auth","-u","theServerAccount","-p","NotSoSecureSecret","80"]
