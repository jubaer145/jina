FROM jinaai/jina:test-pip

WORKDIR /

RUN apt-get update && \
    apt-get install --no-install-recommends -y git \
                                               curl

RUN python -m pip install --no-cache-dir --upgrade pip && \
    git clone https://github.com/jina-ai/jinad.git -b adapt-to-runtime && \
    pip install $(grep -ivE "jina" jinad/requirements.txt)

COPY . /

COPY tests/integration/jinad/test_index_query/entrypoint.sh .

RUN chmod +x entrypoint.sh

ENTRYPOINT ["bash", "-c", "./entrypoint.sh"]
