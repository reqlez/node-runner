.PHONY: install
install:
	$(shell chmod +x add-version.sh)
	$(shell ./add-version.sh)
	pip install pipenv
	pipenv requirements > requirements.txt

.PHONY: output
output-ubuntu-focal: install
	DOCKER_BUILDKIT=1 docker build --output type=local,dest=out/ubuntu/focal --progress plain -f Dockerfile.ubuntufocal  .

output-ubuntu-jammy: install
	DOCKER_BUILDKIT=1 docker build --output type=local,dest=out/ubuntu/jammy --progress plain -f Dockerfile.ubuntujammy  .

.PHONY: local
local: install
	pip install -r requirements.txt

.PHONEY: cmds-reference
cmds-reference: local
	./generate-cmds-help.sh
