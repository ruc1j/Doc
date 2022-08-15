FROM python:3.7.13-alpine

WORKDIR /app/api

COPY ./backend/requirements.txt requirements.txt

RUN apk update \ 
    && apk upgrade \
    && apk --no-cache add musl-dev \
    gcc \
    g++ \
    libffi-dev


# requirements.txtにリストされたパッケージをインストールする
RUN pip install --upgrade pip \
    && pip install --no-cache-dir --trusted-host pypi.python.org -r requirements.txt

# ADD main.py ./backend/
# FastAPIを8000ポートで待機
CMD ["uvicorn", "main:app", "--reload", "--host", "0.0.0.0", "--port", "8000"]