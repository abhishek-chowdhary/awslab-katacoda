## Create an AWS ECR repository and push image to it.


Run the following command to create an ecr-repo.
  
  `aws ecr create-repository --repository-anme <Repo-name>`{{execute}}

Now login in to aws ecr from cli using below command.

   `$(aws ecr get-login --no-include-email --region us-east-1)`{{execute}}

Let's Build the docker image using below command.

    `docker build -t ecs-flask-app .`{{execute}}

Now let's tag the locally built docker image.

    `docker tag ecs-flask-app:latest <ecr-repo-name-as-in-aws-ecr-console>`{{execute}}

Let's push the docker image to ecr repo now.

   `docker push <ecr-repo-name-as-in-aws-ecr-console>`{{execute}}

