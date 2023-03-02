FROM python:3.9

# create working directory inside the container
WORKDIR  /app

# enable the port for the container
EXPOSE 5050

# copy required files to working directory
COPY Pipfile Pipfile.lock ./

# install pipenv to get packages 
# no need to create virtual env, container has a single purpose
RUN pip install pipenv

# install required packages [but not dev-packages]
RUN pipenv requirements > requirements.txt
RUN pip install -r requirements.txt

# layers are cached, so better copy remaining files here for optimization
COPY . ./

# run
CMD ["python", "main.py"]