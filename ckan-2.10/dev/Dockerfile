FROM ckan/ckan-base:2.10.3


ENV APP_DIR=/srv/app
ENV SRC_EXTENSIONS_DIR=/srv/app/src_extensions

# Install packages needed by the dev requirements
RUN apk add --no-cache libffi-dev

# Install CKAN dev requirements
RUN pip3 install -r https://raw.githubusercontent.com/ckan/ckan/${GIT_BRANCH}/dev-requirements.txt

# Create folder for local extensions sources
RUN mkdir -p ${SRC_EXTENSIONS_DIR}

# These are used to run https on development mode
COPY setup/unsafe.cert setup/unsafe.key ${APP_DIR}

COPY setup/start_ckan_development.sh ${APP_DIR}

CMD ["/srv/app/start_ckan_development.sh"]
