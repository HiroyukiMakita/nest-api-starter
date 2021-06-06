# --------------------------------------------------------------- imports
include .env
PROJECT_ROOT := ${ROOT}

# ------------------------------------------------------------- variables
COMPOSE := docker-compose
BUILD := $(COMPOSE) build
LOGS := $(COMPOSE) logs
UP := $(COMPOSE) up -d
DOWN := $(COMPOSE) down
EXEC = $(COMPOSE) exec $(CONTAINER) bash $(ARG)
CONTAINER =
ARG = 

# docker services
NEST := nest

# --------------------------------------------------------- make commands
build:
	@$(BUILD)
logs:
	@$(LOGS)
build-up:
	@$(BUILD) && $(UP)
up:
	$(eval CONTAINER := $(NEST))
	@$(UP)
down:
	@$(DOWN)
destroy:
	@$(DOWN) --rmi all --volumes --remove-orphans
exec-nest:
	$(eval CONTAINER := $(NEST))
	$(eval ARG := -c "cd $(PROJECT_ROOT) && bash")
	@$(EXEC)
start-nest:
	$(eval CONTAINER := $(NEST))
	$(eval ARG := -c "cd $(PROJECT_ROOT) && npm start && bash")
	@$(EXEC)
create-nest-app-current:
	$(eval CONTAINER := $(NEST))
	$(eval ARG := -c "\
	cd $(PROJECT_ROOT) && \
	nest new nest-app --package-manager npm && \
	cat nest-app/.gitignore >> $(PROJECT_ROOT)/.gitignore && \
	shopt -s dotglob && \
	mv -n nest-app/* . && \
	shopt -u dotglob && \
	rm -r nest-app\
	")
	$(EXEC)
nest-app-destroy:
	$(eval CONTAINER := $(NEST))
	$(eval ARG := -c "\
	cd $(PROJECT_ROOT) && \
	rm -r dist/ node_modules/ src/ test/ .eslintrc.js .prettierrc nest-cli.json package* tsconfig* ; \
	cat .gitignore.example > .gitignore\
	")
	$(EXEC)