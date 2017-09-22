# Prerequisites

Follow this guide to prepare you Google Cloud Project and deployment machine.

## Setting up your Google Cloud Project

1. [Sign up](https://cloud.google.com/compute/docs/signup) for Google Cloud Platform
1. Create a [new project](https://console.cloud.google.com/iam-admin/projects)
1. Enable the [Cloud Resource Manager API](https://console.cloud.google.com/apis/api/cloudresourcemanager.googleapis.com/overview)
1. Enable [billing](https://support.google.com/cloud/answer/6293499?hl=en#enable-billing)
1. Determine a [region](https://cloud.google.com/compute/docs/regions-zones/regions-zones) for your deployment (eg: us-east1) and take note of it. In general it's best to pick a region closest to your users.
1. Verify your [existing quota](https://console.cloud.google.com/iam-admin/quotas) for the following resources and file a [quota increase](https://cloud.google.com/compute/quotas) of necessary
   - Persistent Disk Standard (GB) (in desired region): 10,000 GB
   - CPUs (in desired region): 200

## Setting up your Deployment Machine

### Option 1: Using Cloud Shell

Cloud Shell already includes many of the dependencies and is an excellent way to get started. 

1. Open the [Google Cloud Console](https://console.cloud.google.com)
1. Ensure your project is active (See the Project Info section)
1. Click on the `>_` icon in the upper right corner
1. Paste the following snippet into the console to install [terraform](https://www.terraform.io) and the [cf cli](https://github.com/cloudfoundry/cli) to your local user directory:

   ```bash
   mkdir -p bin
   cd bin
   curl -o /tmp/terraform.zip https://releases.hashicorp.com/terraform/0.10.6/terraform_0.10.6_linux_amd64.zip
   unzip /tmp/terraform.zip terraform
   curl -L -o /tmp/cf.tgz "https://cli.run.pivotal.io/stable?release=linux64-binary&source=github"
   tar zxf /tmp/cf.tgz cf
   export PATH=$PATH:~/bin
   ```
   
The machine that hosts your Cloud Shell session is ephemeral but your user directory will be restored for future sessions.


**> With these prerequisites installed you can move on to [Setting up DNS](./dns.md)**

### Option 2: Running Locally

A Linux or Mac machine is required with the following dependencies installed:

- [gcloud](https://cloud.google.com/sdk/downloads)
- [terraform](https://www.terraform.io/downloads.html) (v0.9.11+)
- dig
  - Debian/Ubuntu: `sudo apt-get install dnsutils`
  - OSX: preinstalled
- [go](https://golang.org/doc/install) (v1.8+)
- [cf](https://github.com/cloudfoundry/cli#installers-and-compressed-binaries)
- [sshuttle](https://github.com/apenwarr/sshuttle)
  - Debian/Ubuntu: `sudo apt-get install sshuttle`
  - OSX: `pip install sshuttle`
- [git](https://git-scm.com/downloads)

**> With these prerequisites installed you can move on to [Setting up DNS](./dns.md)**