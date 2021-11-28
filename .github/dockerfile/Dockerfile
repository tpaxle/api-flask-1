FROM python:3.7.12

LABEL maintainer="POC VMW"

RUN mkdir /src/
COPY ./ /src/

RUN useradd -u 1001 -ms /bin/bash app

RUN chown -R 1001 /src \
  && chmod -R "g+rwX" /src \
  && chown -R 1001:root /src

RUN rm -Rf /src/tests && pip install -r src/requirements.txt

WORKDIR /src

EXPOSE 5000
USER 1001

ENV FLASK_ENV=production
ENV SECRET_KEY=YOURSECRETKEY
ENV SQLALCHEMY_DATABASE_URI=mysql+pymysql://root:my-secret-pw@mysql/test

ENTRYPOINT ["python3", "wsgi.py"]
# ENTRYPOINT [ "gunicorn", \
#   "--capture-output", \
#   "--log-level=debug", \
#   "-k eventlet", \
#   "-w 1", \
#   "--bind", \Mu
#   "0.0.0.0:5000", \
#   "app:create_app()"]
