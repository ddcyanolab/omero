FROM openmicroscopy/omero-server:5.6
MAINTAINER ome-devel@lists.openmicroscopy.org.uk

RUN cd /opt/omero/server/ && \
    /opt/omero/server/venv3/bin/omego download -q --release 5.6 server --sym auto

USER root

# OMERO.py plugins
RUN wget https://raw.githubusercontent.com/ome/omero-figure/master/omero_figure/scripts/omero/figure_scripts/Figure_To_Pdf.py -O /opt/omero/server/OMERO.server/lib/scripts/omero/figure_scripts/Figure_To_Pdf.py
RUN /opt/omero/server/venv3/bin/python -m pip install \
    omero-cli-render \
    omero-metadata   \
    reportlab        \
    markdown

USER omero-server

EXPOSE 4063 4064
VOLUME ["/OMERO", "/opt/omero/server/OMERO.server/var"]
