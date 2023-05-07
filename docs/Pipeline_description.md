## Pineline

### Step build:
- node/install install node and checkout code
- Use root level package.json to install dependencies in the frontend app
- Use root level package.json to install dependencies in the backend API
- Lint the frontend
- Build the frontend app
- Build the backend API   
### Step deploy step will run only after manual approval:
- Install, build, deploy in both apps
            
### workflows:
```json
  udagram:
    jobs:
      - build
      - hold:
          filters:
            branches:
              only:
                - master
          type: approval
          requires:
            - build
      - deploy:
          requires:
            - hold
```