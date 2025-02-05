# Dockerfile Bug: Missing Application Files

This repository demonstrates a common error in Dockerfiles: the `CMD` instruction failing because the specified application files are not present in the image.

## Bug Description
The provided Dockerfile attempts to run a Python application using `python3 /app/main.py`. However, the `/app/main.py` file is not included in the image, leading to a runtime error.  The `requirements.txt` file is also not added and it is not clear if it is needed. 

## Bug Solution
The solution involves copying the necessary application files into the image before the `CMD` instruction.  The `requirements.txt` file is included in the solution as well, but this might not be needed. We also add a `WORKDIR` instruction for better clarity.

## How to Reproduce
1. Clone this repository.
2. Build the Docker image using the provided Dockerfile: `docker build -t my-app .`
3. Try to run the image: `docker run my-app` (this should fail)
4. Use the Dockerfile-solution to fix the problem.