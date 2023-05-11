
FROM python:3.12.0a7


WORKDIR /app


VOLUME /app


COPY requirements.txt requirements.txt


RUN pip3 install -r requirements.txt


COPY . .


EXPOSE 5000


CMD ["python3", "-m" , "flask", "--app", "main.py", "run", "--host=0.0.0.0"]
