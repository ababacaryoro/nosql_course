# Use the base Jupyter Notebook image
FROM jupyter/base-notebook

# Install libraries
COPY requirements.txt requirements.txt
RUN pip install --upgrade pip
RUN pip install  -r requirements.txt


# Install extra packages if needed
RUN pip install matplotlib scikit-learn

# Copy your notebooks into the container
COPY ./notebooks /home/jovyan/work
