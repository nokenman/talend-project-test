FROM eclipse-temurin:17
ARG USERNAME=studio
ENV JAVA_OPTS="${talend.job.jvmargs}"
COPY /maven /maven/
WORKDIR /maven/${talend.job.finalName}/${talend.job.name}
RUN useradd -m -s /bin/bash $USERNAME
RUN chown -R $USERNAME:$USERNAME /maven
RUN chmod +x /maven/${talend.job.finalName}/${talend.job.name}/${talend.job.name}_run.sh
RUN sed -i -e 's/ -Xms[0-9]*M//g' -e 's/-Xmx[0-9]*M/$JAVA_OPTS/g' /maven/${talend.job.finalName}/${talend.job.name}/${talend.job.name}_run.sh
ENTRYPOINT ["./${talend.job.name}_run.sh"]
USER studio
