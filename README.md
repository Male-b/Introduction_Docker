# Bar Archive

A system for tracking alcohol beverages.

## Run Locally

Clone the project

```bash
  git clone https://github.com/Singatha/bar-archive.git
```

To run the project, go to the project folder

```bash
  cd bar-archive
```
and run

```bash
  docker-compose up --build
```

for linux prefix with sudo

```bash
  sudo docker-compose up --build
```

To compose down run

```bash
  docker-compose down
```

To compose down run and remove images

```bash
  docker-compose down --rmi all
```

To compose down run, remove images and volumes

```bash
  docker-compose down -v --rmi all
```

## Authors

- [@singatha](https://www.github.com/singatha)

## Roadmap

- Adding endpoints
- Error handling
- Authentication
- Caching
- Security

## Installation

To install dependencies

```bash
  cd bar-archive-service
```

create a virtual environment, if you don't have one setup

```bash
  python3 -m venv venv
```

and then activate the virtual environment

```bash
  source venv/bin/activate
```

install the dependencies

```bash
  pip install -r requirements.txt
```

You can deactivate the virtual environment by running this 

```bash
  deactivate
```

## Adding a new dependency

Activate virtual environment, if has been activated, then install package

```bash
  pip install <package-name>
```

update the requirements file

```bash
  pip freeze > requirements.txt
```

## Compiling Protobufs

after creating the proto files, you can compile them by running this command

```bash
  python3 -m grpc_tools.protoc -I=../bar-archive-protos --python_out=./compiled_protos/ --grpc_python_out=../compiled_protos ../bar-archive-protos/bar_archive.proto
```

change the import statement on 
```bash
  *_grpc.py
```
file, from

```bash
    import bar_archive_pb2 as bar_archive__pb2
```
to

```bash
    from . import bar_archive_pb2 as bar_archive__pb2
```

## Generating Models

To generate models, run thhis command

```bash
  sqlacodegen postgresql://<user>:<password>@<server-IP-Address>/<database-name> --outfile ./models/db.py
```

```bash
  sqlacodegen postgresql://postgres:example@psql-bar-archive-service-db/barArchiveDB --outfile ./models/db.py
```
