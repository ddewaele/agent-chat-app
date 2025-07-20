# Agent App

Sample project based on `create-agent-chat-app`  

```
npx create-agent-chat-app@latest
```


## Development

## Dockerfile

you can generate a dockerfile using the command `npx @langchain/langgraph-cli dockerfile ./Dockerfile` 

It will look like this
```
FROM langchain/langgraphjs-api:20
ADD . /deps/agent-chat-app
ENV LANGSERVE_GRAPHS='{"agent":"./apps/agents/src/react-agent/graph.ts:graph"}'
WORKDIR /deps/agent-chat-app
RUN npm ci
RUN (test ! -f /api/langgraph_api/js/build.mts && echo "Prebuild script not found, skipping") || tsx /api/langgraph_api/js/build.mts
```

Other commands

```
npx @langchain/langgraph-cli dev
npx @langchain/langgraph-cli build
```