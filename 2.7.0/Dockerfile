FROM openjdk:8

# remove several traces of debian python
RUN apt-get purge -y python.*

ENV JYTHON_VERSION="2.7.0" \
    JYTHON_SHASUM="b08d73b5df7d95e35e7b8dcaf1558025cf24f0f1"

RUN curl -fSL -o jython_installer.jar "http://search.maven.org/remotecontent?filepath=org/python/jython-installer/${JYTHON_VERSION}/jython-installer-${JYTHON_VERSION}.jar" \
 && echo "$JYTHON_SHASUM *jython_installer.jar" | shasum -c - \
 && java -jar jython_installer.jar -s -d /usr/local/jython \
 && rm jython_installer.jar \
 && ln -s /usr/local/jython/bin/jython /usr/local/jython/bin/python \
 && ln -s /usr/local/jython/bin/jython /usr/local/jython/bin/python2

ENV PATH="/usr/local/jython/bin:$PATH"
CMD ["jython"]
