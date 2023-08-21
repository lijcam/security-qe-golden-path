# Running the Secure Build Pipeline

Our pipeline is designed to be triggered by an `EventListener`. If you'd like to demonstrate without the webhook integration or test a `PipelineRun`, you can use the minimum required data. In this example, we'll build a .NET Core app from the https://github.com/lijcam/tailspin-tekton-ci Git repository. Be sure to customise the variables according to your specific use case.

Here's a breakdown of the variables and their example data:

| Item              | Example data
| -                 | -
| COMMIT_SHA	    | ded0b5f379b150e27eb959f115361029e4f2387a
| TLSVERIFY	        | false
| BUILD_EXTRA_ARGS  | “”
| IMAGE_REPO        | quay.io/lijcam/space-game-web
| IMAGE_TAG	        | head-ded0b5f379b150e27eb959f115361029e4f2387a
| IMAGE_DOCKERFILE  | ./Tailspin.SpaceGame.Web/Dockerfile
| IMAGE_CONTEXT_DIR	| ./Tailspin.SpaceGame.Web
| GIT_REF           | HEAD
| COMMIT_DATE       | 2023-08-16
| COMMIT_AUTHOR	    | Liam Campbell
| COMMIT_MESSAGE    | Testing test
| GIT_REPO          | https://github.com/lijcam/tailspin-tekton-ci

These variables will guide the pipeline's behavior, ensuring a secure and efficient build process. Don't forget to adapt them to match your unique requirements and repository details.