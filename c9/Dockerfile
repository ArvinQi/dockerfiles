# Cloud9 server
# A lot inspired by sapk

FROM alpine

RUN apk -U --no-cache --no-progress upgrade \
    && apk -U --no-cache --force --no-progress add bash nodejs nodejs-npm yarn tmux git make gcc g++ python sqlite wget openssl ca-certificates \
    && npm install -g forever && npm cache clean --force \
    && git clone --depth=5 https://github.com/c9/core.git /root/.c9 && cd /root/.c9 \
    && mkdir -p ./node/bin ./bin ./node_modules \		
    && ln -sf "`which tmux`" ./bin/tmux \		
    && ln -s "`which node`" ./node/bin/node \		
    && ln -s "`which npm`" ./node/bin/npm \
    && npm install pty.js \
    && echo 1 > ./installed \
    && NO_PULL=1 ./scripts/install-sdk.sh \
    && npm cache clean --force && rm -rf /var/cache/apk/* /tmp/* /var/tmp/* \
    && git reset --hard


VOLUME /workspace
EXPOSE 8181 
ENTRYPOINT ["forever", "/root/.c9/server.js", "-w", "/workspace", "--listen", "0.0.0.0"]

CMD ["--auth","c9:c9"]