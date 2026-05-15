# Ttrend application

This is a small application with `main` and `test` folders.

- `main` contains application code.
- `test` contains test cases.
- `pom.xml` contains all dependencies, artifact name, and version.

## Maven setup

### Download Maven

```bash
sudo wget https://archive.apache.org/dist/maven/maven-3/3.9.2/binaries/apache-maven-3.9.2-bin.tar.gz
```

### Extract Maven

```bash
sudo tar -xvzf apache-maven-3.9.2-bin.tar.gz
ls /opt
```

You should see:

- `apache-maven-3.9.2`
- `apache-maven-3.9.2-bin.tar.gz`

### Configure Maven

```bash
sudo tee /etc/profile.d/maven.sh > /dev/null <<'EOF'
export M2_HOME=/opt/apache-maven-3.9.2
export PATH="${M2_HOME}/bin:${PATH}"
EOF

source /etc/profile.d/maven.sh
```

### Verify Maven

```bash
mvn -version
```

Expected output should include:

- `Apache Maven 3.9.2`
- `Java version: 11`

## Jenkins GitHub webhook setup

### Step 1: Install GitHub plugins

In Jenkins:

- Manage Jenkins
- Manage Plugins
- Installed Plugins

Verify the following plugins are installed:

- Git Plugin
- GitHub Integration Plugin

If any are missing:

- Go to Available Plugins
- Install the missing plugins
- Restart Jenkins

### Step 2: Configure Jenkins job for webhook trigger

In your Pipeline job configuration:

- Go to Build Triggers
- Select `GitHub hook trigger for GITScm polling`
- Save

### Step 3: Configure GitHub webhook

In GitHub:

- Open your repository
- Go to `Settings` → `Webhooks`
- Click `Add webhook`

### Step 4: Add webhook URL

Use the following Payload URL:

```text
http://<JENKINS-PUBLIC-IP>:8080/github-webhook/
```

Example:

```text
http://13.233.xx.xx:8080/github-webhook/
```

Important:

- URL must end with `/github-webhook/`
- Do not forget the trailing slash

### Step 5: Configure webhook settings

Set:

- Content type: `application/json`
- Secret: Leave empty
- SSL verification: Disable if using HTTP
- Events: `Just the push event`

Then click `Add webhook`.

### Step 6: Open AWS security group

Allow inbound ports:

- Custom TCP: `8080`
- SSH: `22`

Source:

- `0.0.0.0/0`

### Step 7: Test webhook

```bash
git add .
git commit -m "webhook test"
git push origin main
```

Jenkins build should start automatically.

### Step 8: Verify webhook delivery

In GitHub:

- Go to `Settings` → `Webhooks` → `Recent Deliveries`
- Confirm the delivery shows `200 OK`
