FROM python:3.12-slim-bullseye

ENV POETRY_VERSION 1.4.1

# Install system dependencies in China
#国内服务器没有代理的情况下用这个镜像源
RUN pip install -i https://pypi.tuna.tsinghua.edu.cn/simple "poetry==$POETRY_VERSION"
# Install system dependencies other country
#有代理可以直接用下面的镜像源
#RUN pip install "poetry==$POETRY_VERSION"

# Set work directory
WORKDIR /app

# Copy only requirements to cache them in docker layer
COPY poetry.lock pyproject.toml /app/

# Disable the creation of virtual environments
RUN poetry config virtualenvs.create false

# Install dependencies
RUN poetry install

# Copy the current directory contents into the container at /app
COPY ./ /app/
