# Stage 1: Builder
FROM python:3.10-alpine AS builder

WORKDIR /app

COPY requirements.txt /app
RUN apk add --no-cache build-base && \
    pip3 install --prefix=/install -r requirements.txt

# Stage 2: Final image
FROM python:3.10-alpine

WORKDIR /app

# Copy the installed dependencies from the builder stage
COPY --from=builder /install /usr/local

COPY . /app

ENTRYPOINT ["python3"]
CMD ["app.py"]

