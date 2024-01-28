FROM python:3.10-slim-buster

# Inside Container
# Make new folder inside the container
WORKDIR /backend-flask

# Ourside Container -> Inside the Container
# This contains the librabries we want to install to run the app
COPY requirements.txt requirements.txt

# Inside Container
# Install the Python libraries used for the app
RUN pip3 install -r requirements.txt

# Outside -> Inside
# . means everything in the current directory
# First . for everything /backend-flask (outside)
# Second . for everything /backend-flask (inside)
COPY . .

# Set Env Var
# This is inside the container
ENV FLASK_ENV=development

EXPOSE ${PORT}

# Run CMD command for Python Flask
CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0", "--port=4567"]
