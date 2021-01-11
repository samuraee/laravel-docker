FROM edbizarro/gitlab-ci-pipeline-php:7.4

USER root

RUN sudo echo $(grep $(hostname) /etc/hosts | cut -f1) $APP_HOST_NAME >> /etc/hosts

USER $IMAGE_USER
