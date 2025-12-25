ARG BASE_IMAGE=python:3.8-slim

FROM ${BASE_IMAGE} AS builder
WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt --prefix=/install

FROM ${BASE_IMAGE}
WORKDIR /app
COPY --from=builder /install /usr/local
COPY application.py /app
ENV PORT=5000
EXPOSE ${PORT}

ENTRYPOINT ["python3"]
CMD ["application.py"]
