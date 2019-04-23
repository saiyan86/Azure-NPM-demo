USER=yonglichenms
ERDIR=expressroute
ERREPO=er-content-demo
ERTAG=onug
FWDIR=firewall
FWREPO=firewall-content-demo
FWTAG=onug

build: build-expressroute build-firewall

build-expressroute:
	docker build -t $(USER)/$(ERREPO):$(ERTAG) $(ERDIR)

build-firewall:
	docker build -t $(USER)/$(FWREPO):$(FWTAG) $(FWDIR)

push:
	docker push $(USER)/$(ERREPO):$(ERTAG)
	docker push $(USER)/$(FWREPO):$(FWTAG)

pull:
	docker pull $(USER)/$(ERREPO):$(ERTAG)
	docker pull $(USER)/$(FWREPO):$(FWTAG)