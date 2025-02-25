# Use an official Python runtime as a parent image
FROM python:3.9-slim

# Set the working directory to root
WORKDIR /

# Install git, bash, and other useful tools
RUN apt-get update && apt-get install -y \
    git \
    bash \
    tree \
    && rm -rf /var/lib/apt/lists/*

# Set bash as the default shell
SHELL ["/bin/bash", "-c"]
RUN pip install jupyterlab
# Optional: Configure git with default user
RUN git config --global user.name "rishav1305" && \
    git config --global user.email "rishav.chatt@gmail.com"

# RUN git config --global url."git@github.com:".insteadOf "https://github.com/"

RUN git clone https://github.com/rishav1305/AI_Agent.git
# RUN git clone https://github.com/rishav1305/Automated-DSA.git
RUN pip install -r AI_Agent/requirements.txt

RUN apt-get -y update; apt-get -y install curl
RUN curl -fsSL https://ollama.com/install.sh | sh
EXPOSE 8888

# Start Jupyter Notebook
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
