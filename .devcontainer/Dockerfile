#Use an official Python runtime as the base image
FROM python:3.11

#Set the working directory in the container
#change name to folder on personal repo in case of personal project
WORKDIR /app/mlpark

#Install git to clone the repository
RUN apt-get update && apt-get install -y git

#Copy 
COPY . .

#Create a venv and activate it
RUN python -m venv /opt/venv/snowpark-env
ENV PATH="/opt/venv/snowpark-env/bin:$PATH"

#Install required packages within the venv
#You might need to edit the requirements file depending on the packages you need
RUN pip install --no-cache-dir -r requirements.txt
RUN pip install jupyter ipykernel

#Set up the Jupyter kernel
#In case of own project set up new 
RUN python -m ipykernel install --name "snowpark" --display-name "Snowpark Kernel"

#Expose the port for Jupyter notebook
EXPOSE 8888

#start Jupyter notebook
CMD ["jupyter", "notebook", "--ip=0.0.0.0", "--port=8888", "--no-browser", "--allow-root"]
