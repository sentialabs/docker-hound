FROM python:3.6

RUN mkdir -p /usr/src/app
RUN git clone https://github.com/houndci/python /usr/src/app \
    && cd /usr/src/app \
    && git reset --hard 7a4d9cffa1d499fb415b2f20f7ed714cfe27c07c
WORKDIR /usr/src/app

RUN pip install -U -r requirements.txt

CMD PYTHONPATH=$(pwd):$PYTHONPATH ./worker.py python_review
