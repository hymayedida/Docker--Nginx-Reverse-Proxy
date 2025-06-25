FROM docker.io/python:3.13-rc-slim
ENV PYTHONUNBUFFERED=1 \
 PYTHONDONTWRITEBYTECODE=1 \
 PYTHON_BIN=python3
WORKDIR /app
RUN apt-get update && \
 apt-get install -y curl build-essential git && \
 ${PYTHON_BIN} -m ensurepip && \
 ${PYTHON_BIN} -m pip install --upgrade pip && \
 curl -Ls https://astral.sh/uv/install.sh | bash && \
 cp $HOME/.local/bin/uv /usr/local/bin/uv
COPY pyproject.toml ./
RUN uv pip install --system .
COPY app.py ./
EXPOSE 8002
CMD ["python", "app.py"]

