FROM node:21-bookworm AS base
# RUN apt-get update && apt-get install -y python3 python3-pip python3-venv
WORKDIR /app
COPY ./packages/ml/requirements.txt ./packages/ml/
# RUN python3 -m venv ./packages/ml/venv
# RUN . packages/ml/venv/bin/activate && pip3 install -r ./packages/ml/requirements.txt
COPY package.json package-lock.json ./
COPY packages/frontend/package.json packages/frontend/
COPY packages/backend/package.json packages/backend/
COPY packages/shared/package.json packages/shared/
RUN npm ci
COPY ./packages ./packages
RUN npm run build:frontend

CMD ["npm", "run", "start"]
