# DO NOT EDIT!
# This file  was auto-generated with ./sync.sh at Thu Jun 13 22:51:40 CEST 2019

FROM ubuntu:artful
LABEL MAINTAINER "Mathias Lüdtke" <mathias.luedtke@ipa.fraunhofer.de>
RUN sed -i -re 's/([a-z]{2}.)?archive.ubuntu.com|security.ubuntu.com/old-releases.ubuntu.com/g' /etc/apt/sources.list

ENV ROS_DISTRO melodic

RUN echo 'debconf debconf/frontend select Noninteractive' | debconf-set-selections

RUN apt-get update -qq     && apt-get -qq install --no-install-recommends -y apt-utils gnupg wget ca-certificates lsb-release dirmngr

RUN echo "deb http://snapshots.ros.org/melodic/final/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list
RUN for i in 1 2 3; do { apt-key adv --keyserver 'hkp://keyserver.ubuntu.com:80' --recv-key 'AD19BAB3CBF125EA'; } &&  break || sleep 1; done

RUN sed -i "/^# deb.*multiverse/ s/^# //" /etc/apt/sources.list     && apt-get update -qq     && apt-get -qq install --no-install-recommends -y         build-essential         python-catkin-tools         python-pip         python-rosdep         python-wstool         ros-melodic-catkin         ssh-client     && apt-get clean     && rm -rf /var/lib/apt/lists/*
