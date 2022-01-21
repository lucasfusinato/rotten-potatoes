FROM python:3.8-slim-buster
WORKDIR /usr/src/app
COPY requirements.txt .
RUN python -m pip install -r requirements.txt
COPY . .
EXPOSE 5000
RUN addgroup --system app && adduser --system --group app && chown -R app /usr/src/app
USER app
CMD ["gunicorn", "--workers=3", "--bind", "0.0.0.0:5000", "-c", "config.py", "app:app"]