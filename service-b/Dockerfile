FROM python:3.9-slim
WORKDIR /app
COPY . /app
RUN pip install flash
EXPOSE 5000
ENV NAME world
CMD [ "python", "app.py" ]
