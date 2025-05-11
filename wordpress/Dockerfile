FROM bitnami/wordpress-nginx:6.8.1-debian-12-r1

# Switch to root to install system dependencies
USER root

# Install Python, pip, and create a virtual environment
RUN install_packages python3 python3-pip && \
    python3 -m venv /opt/bitnami/venv && \
    /opt/bitnami/venv/bin/pip install --no-cache-dir sqlalchemy pymysql supabase python-dotenv

# Copy sync scripts into the container
COPY ./scripts /opt/bitnami/scripts

# Copy custom PHP config
COPY 99-upload-size.ini /opt/bitnami/php/etc/conf.d/

# Revert back to Bitnami's default non-root user
USER 1001
