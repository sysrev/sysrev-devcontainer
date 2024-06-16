# Use an official Python runtime as a parent image
FROM python:3.10-slim

# Set the working directory in the container
WORKDIR /usr/src/app

# Install system packages for R
RUN apt-get update && \
    apt-get install -y r-base && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install Python dependencies from requirements.txt
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.csv

# Install R packages
RUN R -e "install.packages(c('tidyverse', 'data.table', 'httr', 'jsonlite'), repos='http://cran.rstudio.com/')"

# Copy the rest of your application into the container
COPY . .

# Command to open a Bash shell when starting your container
CMD ["/bin/bash"]
