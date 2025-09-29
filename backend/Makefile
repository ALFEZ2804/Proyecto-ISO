.PHONY: install run migrate lint test docker-build docker-run

# Instalar dependencias (incluye dev)
install:
	python -m venv .venv && . .venv/bin/activate && pip install -r requirements.txt -r requirements-dev.txt

# Arrancar el backend en local
run:
	uvicorn app.main:app --reload

# Migrar la base de datos
migrate:
	alembic upgrade head

# Lint + formateo check
lint:
	ruff check .
	black --check .

# Tests
test:
	pytest -q

# Construir imagen docker
docker-build:
	docker build -t unigo-api .

# Correr el backend en docker (necesita .env y servicios de infra activos)
docker-run:
	docker run -it --rm -p 8000:8000 --env-file .env unigo-api
