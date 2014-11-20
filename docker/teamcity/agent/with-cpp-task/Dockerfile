FROM ciworks-agent
MAINTAINER Emil Mieilica <emil.mieilica@gmail.com>
USER root

ADD bootstrap-agent.sh \
    https://raw.githubusercontent.com/emil-mi/ciworks/master/cvm/cvm \
    https://raw.githubusercontent.com/emil-mi/ciworks/master/cvm/cvm-exec /usr/local/bin/

ADD https://github.com/emil-mi/cpptasks-parallel/releases/download/cpptasks-parallel-2.0.0/cpptasks-parallel-2.0.0.jar /home/teamcity/.ant/lib/

RUN apt-get update \
    && apt-get install -y ant ant-contrib \
    && rm -rf /var/lib/apt/lists/* \
    && echo "teamcity ALL=(ALL) NOPASSWD:ALL" > /etc/sudoers.d/teamcity \
    && echo "export CLASSPATH=\$(ls -1 ~/.ant/lib | paste -sd ':')" > /home/teamcity/.ant/ant.conf \
    && chown -R teamcity:teamcity /home/teamcity \
    && chmod +rx /usr/local/bin/*

USER teamcity
CMD ["/bin/bash","-i"]