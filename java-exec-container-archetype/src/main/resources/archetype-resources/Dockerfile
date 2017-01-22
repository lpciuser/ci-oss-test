# This Dockerfile create a docker image for creating ${artifactId} containerized application.

# (1) create the base image of lp-jdk8-base
FROM lpdocker-registry.dev.lprnd.net/lp-jdk8-base

# (2) create the application directories
ENV lp_lib_dir /liveperson/code/server_app/lib
RUN mkdir $lp_lib_dir ; chown -R appuser:appgrp $lp_lib_dir ; chmod -R 775 $lp_lib_dir

ENV lp_conf_dir /liveperson/code/server_app/lib
RUN mkdir $lp_conf_dir ; chown -R appuser:appgrp $lp_conf_dir ; chmod -R 775 $lp_conf_dir

ENV lp_bin_dir /liveperson/code/server_app/lib
RUN mkdir $lp_bin_dir ; chown -R appuser:appgrp $lp_bin_dir ; chmod -R 775 $lp_bin_dir

# (3) copy the ${artifactId} application jar file to the 'lib' directory
COPY ${artifactId}-app/target/${artifactId}-jar-with-dependencies.jar $lp_lib_dir/

# (4) copy init script
COPY resources/LP__serviceNameLowerCase__ /etc/init.d/

# (5) start the  service
CMD service LP__serviceNameLowerCase__ start