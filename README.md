This repository provides step-by-step instructions to set up and execute the AI-driven serverless system developed for cold start latency mitigation.

All source code and resources are available in the following GitHub organization:

https://github.com/FinalYearResearch066

Related Repositories

OpenFaaS-Functions
https://github.com/FinalYearResearch066/OpenFaas-Functions

AI Service
https://github.com/FinalYearResearch066/AI-Service

Datasets
https://github.com/FinalYearResearch066/Datasets


System Requirements

* Linux (Ubuntu recommended)
* Docker
* Git
* Python 3.8+

Install and Configure OpenFaaS (faasd)

Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl enable docker
sudo systemctl start docker
```

Install faasd

```bash
curl -sLS https://get.openfaas.com | sudo sh
```

Start faasd

```bash
sudo systemctl start faasd
```

Login to OpenFaaS

```bash
export OPENFAAS_URL=http://127.0.0.1:8080
export PASSWORD=$(sudo cat /var/lib/faasd/secrets/basic-auth-password)

faas-cli login --username admin --password $PASSWORD
```

Deploy Serverless Functions

```bash
git clone https://github.com/FinalYearResearch066/OpenFaas-Functions.git
cd OpenFaas-Functions
faas-cli deploy
```

Run AI Service

```bash
git clone https://github.com/FinalYearResearch066/AI-Service.git
cd AI-Service

python3 -m venv dev/venv
source dev/venv/bin/activate

python3 app.py
```

Dataset Usage

* gru_dataset_fixed_dates_8000.csv for training and Evaluation
* test_data2.csv for testing

System Workflow

1. OpenFaaS functions receive requests
2. AI model predicts upcoming requests
3. Functions are pre-warmed
4. Cold start latency is reduced

Notes

* Ensure Docker is running before faasd


