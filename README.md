# fastapiPET

sudo docker-compose up -d

sudo docker ps

alembic init migrations

alembic revision --autogenerate -m "add users table"

alembic revision upgrade head

alembic upgrade head

uvicorn app.main:app --reload

docker build -t apipet .

docker run -d -p 8000:8000 apipet
