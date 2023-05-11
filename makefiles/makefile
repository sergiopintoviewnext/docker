

tag=latest
nombre_imagen=debian
nombre_contenedor=debian
opciones=-d --name $(nombre_contenedor)

todas= build_run visualizacion eliminacion

build_run: ## Pull de imagen y creacion del contenedor
	@echo "Pull de imagen"
	docker pull $(nombre_imagen):$(tag)
	@echo "Creacion del contenedor"
	docker run $(opciones) $(nombre_imagen):$(tag)
	@echo "Comprobar contenedores"
	docker ps -a


visualizacion: ## Visualizacion de imagenes y contenedores
	@echo "Visualizar imagenes"
	docker image ls
	@echo "Visualizar contenedores en ejecucion"
	docker ps -f status=running
	@echo "Visualizar contenedores parados"
	docker ps -f status=exited
	

eliminacion: ## Eliminazion de imagen y contenedor
	@echo "Deteniendo contenedor $(nombre_contenedor)..."
	docker stop $(nombre_contenedor)
	@echo "Eliminando contendor $(nombre_contenedor)..."
	docker rm -fv $(nombre_contenedor)
	@echo "Eliminar imagen"
	docker rmi $(nombre_imagen)

todas: $(todas) ## Ejecucion de build_run visualizacion eliminacion

.PHONY: help
help:  ## Muestra la ayuda
	@fgrep -h "##" $(MAKEFILE_LIST) | fgrep -v fgrep | sed -e 's/\\$$//' | sed -e 's/##//'