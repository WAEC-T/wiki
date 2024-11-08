### Requiremnets for compose files for `weact` Applications 

#### 1. `compose-test.yml`

**Example forom `python-flask` application**
```code
services:
  python-flask:
    image: waect/python-flask:latest
    build: .
    ports:
      - "5000:5000"
    env_file:
      - ../.env.local
    networks:
      - waect-network

networks:
  waect-network:
    external: true
```

### 2. `compose-prod.yml` 

**Example forom `python-flask` application**
```code
services:
  python-flask:
    image: simonharwick97822/python-flask:latest
    build: .
    container_name: python-flask
    ports:
      - "5000:5000"
    env_file:
      - ../.env.prod
```


