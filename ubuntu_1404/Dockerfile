FROM ubuntu:14.04.2

MAINTAINER Postman Labs <help@getpostman.com>

# Install curl and npm
RUN apt-get update && apt-get install -y \
    curl \
    npm;

# Set node version
ENV NODE_VERSION 0.10.6

# Set newman version
ENV NEWMAN_VERSION 1.2.17

# Install node and newman
RUN npm install -g n && \
    n ${NODE_VERSION} && \
    npm install -g newman@${NEWMAN_VERSION};

# Set workdir to /etc/newman
# When running the image, mount the directory containing your collection to this location
#
# docker run -v <path to collections directory>:/etc/newman ...
#
# In case you mount your collections directory to a different location, you will need to give absolute paths to any
# collection, environment files you want to pass to newman, and if you want newman reports to be saved to your disk.
# Or you can change the workdir by using the -w or --workdir flag

WORKDIR /etc/newman

# Set newman as the default container command
# Now you can run the container via
#
# docker run -v /home/collections:/etc/newman -t newman_ubuntu1404 -c YourCollection.json.postman_collection \
#                                                                  -e YourEnvironment.postman_environment \
#                                                                  -H newman_report.html

ENTRYPOINT ["newman"]
