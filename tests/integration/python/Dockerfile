FROM python:slim@sha256:63bb298d2b7b88f176f51b5189f54ce6535c997682ea70885d2132f5d473a8a5
WORKDIR /code
ENTRYPOINT ["sh", "-c", "if [ -n \"$INSTALL_DEPS\" ]; then eval \"$INSTALL_DEPS\"; fi && python search.py"]
