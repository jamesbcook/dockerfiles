FROM jfloff/alpine-python:2.7

RUN apk add --update git && rm -fr /var/cache/apk/*

RUN git clone https://github.com/gojhonny/InSpy.git
WORKDIR InSpy
RUN chmod +x InSpy.py && pip install -r requirements.txt

ENTRYPOINT ["python", "InSpy.py"]
