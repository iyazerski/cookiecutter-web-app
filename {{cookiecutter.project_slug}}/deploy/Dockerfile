# base image
FROM python:3.9-buster

# add service user
ARG PROJECT_USER
RUN adduser --disabled-password ${PROJECT_USER}
USER ${PROJECT_USER}

# create project dir
ARG PROJECT_ROOT
RUN mkdir ${PROJECT_ROOT}
WORKDIR ${PROJECT_ROOT}
RUN mkdir logs

# install requirements
COPY requirements requirements
ARG VIRTUAL_ENV
RUN python -m venv $VIRTUAL_ENV
ENV PATH="$VIRTUAL_ENV/bin:$PATH"
RUN python -m pip install --upgrade pip setuptools wheel
RUN pip install -r requirements/prod.txt

# copy project files
COPY LICENSE *.py *.in ./
COPY {{ cookiecutter.project_slug }} {{ cookiecutter.project_slug }}
