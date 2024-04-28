# Use multi-stage build to keep the final image clean and small
FROM alpine:3.19.1 as builder

# Install build dependencies
RUN apk add --no-cache git build-base zlib-dev bzip2-dev sqlite-dev readline-dev

# Clone the CPython repository
RUN git clone https://github.com/python/cpython.git

# Configure and build Python
RUN cd cpython && \
    ./configure --prefix=/usr/local/python3 --enable-shared --with-pydebug && \
    make && \
    make install

# Start a new stage from scratch
FROM alpine:3.19.1

# Install runtime dependencies
RUN apk add --no-cache bzip2 sqlite-libs readline

# Copy the Python build from the builder stage
COPY --from=builder /usr/local/python3 /usr/local/python3

# Set environment variables
ENV LD_LIBRARY_PATH="/usr/local/python3/lib:${LD_LIBRARY_PATH}"
ENV PATH="/usr/local/python3/bin:${PATH}"

# Verify Python installation
RUN python3 -V

# Set the entrypoint
ENTRYPOINT ["python3"]
