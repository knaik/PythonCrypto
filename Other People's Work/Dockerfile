FROM jupyter/minimal-notebook:abdb27a6dfbb

#Set the working directory
WORKDIR /home/jovyan/

# Add files
COPY notebooks/include /home/jovyan/notebooks/include
COPY notebooks/*.ipynb /home/jovyan/notebooks/
COPY notebooks/private_key.der /home/jovyan/notebooks/
COPY notebooks/private_key.pem /home/jovyan/notebooks/
COPY notebooks/public_key.der /home/jovyan/notebooks/
COPY solutions/ /home/jovyan/solutions
COPY requirements.txt /
COPY postBuild /home/jovyan/postBuild

# Modules
RUN pip install -r /requirements.txt

# Allow user to write to directory
USER root
RUN chown -R $NB_USER /home/jovyan \
    && chmod -R 774 /home/jovyan \
    && rm -fR /home/jovyan/work \
    && /home/jovyan/postBuild
USER $NB_USER

# Expose the notebook port
EXPOSE 8888
