USER=yonglichenms
ERDIR=expressroute
ERREPO=azure-npm-demo-expressroute
ERTAG=onug
FWDIR=firewall
FWREPO=azure-npm-demo-firewall
FWTAG=onug

build: build-expressroute build-firewall

build-expressroute:
	docker build -t $(USER)/$(ERREPO):$(ERTAG) $(ERDIR)

build-firewall:
	docker build -t $(USER)/$(FWREPO):$(FWTAG) $(FWDIR)

push:
	docker push $(USER)/$(ERREPO):$(ERTAG)
	docker push $(USER)/$(FWREPO):$(FWTAG)