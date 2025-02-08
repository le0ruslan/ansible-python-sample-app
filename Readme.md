<h1>Django App Deployment With Ansible</h1>

<h3>Project Description</h3>

This repository implements the deployment of the application [devops-sample-django-app](https://github.com/simbirsoft/devops-sample-django-app) using Ansible.

## Installation


### Prerequisites

- Install Python 3.8
- Install required libraries
- Install Vagrant

### Setup and Deployment

1. Open the project:
   ```shell
   cd exercise-06
   ```

2. Create and activate a virtual environment:
   ```shell
   python3.8 -m venv venv
   source venv/bin/activate
   ```

3. Install dependencies:
   ```shell
   pip3 install -r requirements.txt
   ```
   ```shell
   ansible-galaxy install -r requirements.yml -p roles/vendor
   ```

4. Start the Vagrant VM:
   ```shell
   vagrant up
   ```

5. Run the Ansible playbook:
   ```shell
   ansible-playbook -i environments/dev/inventory.yml site.yml
   ```

### Verification

1. Check connection on ports 5432 and 5000:
   ```shell
   nc -zv 192.168.56.11 5432
   nc -zv 192.168.56.11 5000
   ```

2. Verify PostgreSQL version:
   ```shell
   vagrant ssh -c "pg_config --version"
   ```

3. Perform a POST request:
   ```shell
   curl -i -X POST -d '{ "username": "user123", "email": "user@example.com", "password_hash": "example" }' -H "Content-Type: application/json" http://192.168.56.11:5000/api/user
   ```

4. Perform a GET request:
   ```shell
   curl -i -X GET http://192.168.56.11:5000/api/user
   ```

5. Restart the VM:
   ```shell
   vagrant ssh -c "sudo reboot"
   ```

6. Verify the application is still running:
   ```shell
   curl -i -X GET http://192.168.56.11:5000/api/user
   ```

## Notes

- Additional tasks were not completed.

