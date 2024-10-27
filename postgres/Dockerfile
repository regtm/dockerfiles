FROM pgvector/pgvector:pg16

# Install certificates and add apt.postgresql.org repository
RUN apt-get update && \
    apt-get install -y \
    expect \
    postgresql-common && \
    expect -c 'spawn /usr/share/postgresql-common/pgdg/apt.postgresql.org.sh; expect "Press Enter to continue, or Ctrl-C to abort."; send "\r"; interact'

# Install plpython, numpy, and scikit-learn
RUN apt-get update && \
    apt-get install -y \
    postgresql-plpython3-16 \
    python3-numpy \
    python3-sklearn && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*
    
ENV max_locks_per_transaction=2048
ENV max_wal_size='8GB'
ENV shared_buffers='10GB'
ENV max_connections=256

# Set the default command to run when starting the container
CMD ["postgres"]
