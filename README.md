# Deploy to a Linux server using rsync 

```python
name: Deploy to Server 

on:
  push:
    branches:
      - developemnt # Change this to match your branch name

jobs:
  deploy:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout code
      uses: actions/checkout@v2
    - name: deploy to server
      uses: sparkouttech/ssh-deployment@v2
      env:
          DEPLOY_KEY: ${{ secrets.SERVER_SSH_KEY }}
          ARGS: "-avz --delete"
          SERVER_PORT: ${{ secrets.SERVER_PORT }}
          FOLDER: "./"
          SERVER_IP: ${{ secrets.SERVER_IP }}
          USERNAME: ${{ secrets.USERNAME }}
          SERVER_DESTINATION: ${{ secrets.SERVER_DESTINATION }}
```
