FROM python:3

RUN apt update \
 && apt install -y \
 wget \
 vim \
 libgeos-dev \
 && rm -rf /var/lib/apt/lists/*


# Set an environment variable with the directory
# where we'll be running the app
ENV APP /app

# Create the directory and instruct Docker to operate
# from there from now on
RUN mkdir $APP
WORKDIR $APP

# Expose the port uWSGI will listen on
EXPOSE 5000

# Copy the requirements file in order to install
# Python dependencies
COPY requirements.txt .

## install miniconda
#RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
#RUN bash Miniconda3-latest-Linux-x86_64.sh -b -p /miniconda
#ENV PATH=$PATH:/miniconda/condabin:/miniconda/bin

# Install Python dependencies
RUN pip install -r requirements.txt

# We copy the rest of the codebase into the image
COPY . .


# Finally, we run uWSGI with the ini file we
# created earlier
CMD [ "uwsgi", "--ini", "app.ini" ]

