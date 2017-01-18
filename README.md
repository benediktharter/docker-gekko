
# docker-gekko

Docker configuration for [gekko traiding bot](https://github.com/askmike/gekko)

Pull docker image: `docker pull ivan1993spb/gekko`

## docker-compose.yml

```yml
version: '2'

services:

  postgres:
    image: postgres
    restart: always
    environment:
      - POSTGRES_USER=user
      - POSTGRES_PASSWORD=pass
    volumes:
      - postgres_data:/var/lib/postgresql/data

  gekko:
    image: ivan1993spb/gekko
    restart: always
    volumes:
      - gekko_history:/gekko/history
      # create your gekko config here
      # - ./config.js:/gekko/config.js
    depends_on:
      - postgres

volumes:
  gekko_history:
  postgres_data:

```
