
---
Discord Bot for Clash of Clans War Updates

## Deploy
Clone the Repository and build the Docker Image
```
docker build
```
Start the Docker Stack
```
docker-compose -f docker-compose-portainer.yml up 
```

## Dev
```
npm run start:dev
```

## Env file
```
NODE_ENV=production
DATABASE_URL=postgres://<username:password>@<ip:5432>/<db>
DISCORD_BOT_TOKEN=discord application token
DISCORD_GUILD_ID=discord server id
DISCORD_WAR_LOG_CHANNEL=discord channel id for war updates
DISCORD_WAR_ATTACKS_CHANNEL=discord channel id for attack updates
COC_API_TOKEN=coc api token
COC_CLAN_TAG=coc clan tag
LOGGING_LEVEL=debug
LOGGING_FORMAT=default
POSTGRES_USER=
POSTGRES_PASSWORD=
```