# a basic Dockerfile with emacs - fewer layers

FROM ubuntu:20.04

label maintainer "glenn opdycke-hansen"

RUN apt-get update \
	&& apt-get upgrade -y \
	&& apt-get install -y emacs

