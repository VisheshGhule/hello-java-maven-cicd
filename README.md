# Jenkins Maven Build – Hello Java Maven CICD

## 📌 Overview
This project demonstrates setting up a **Jenkins Freestyle job** to build a simple Maven-based Java application from a GitHub repository.  
The goal was to:
- Install and configure Jenkins with the required plugins
- Configure Maven in Jenkins
- Pull code from GitHub
- Build the project using Maven
- Successfully produce a `.jar` file

---

## 🛠 Prerequisites
Before starting, ensure you have:
- **Jenkins** installed and running
- **Git** installed
- **Maven** installed or configured inside Jenkins
- A **GitHub repository** with a valid `pom.xml` file and Java source code
<img width="550" height="158" alt="Screenshot from 2025-08-15 16-50-31" src="https://github.com/user-attachments/assets/7663ec0d-8c57-45e8-ae3b-caa57bc72db2" />
<br><br>
<img width="700" height="185" alt="Screenshot from 2025-08-15 16-50-55" src="https://github.com/user-attachments/assets/06208eb7-39be-417f-a05c-a39bcb6a4c8f" />
<br><br>
<img width="900" height="117" alt="Screenshot from 2025-08-15 17-09-43" src="https://github.com/user-attachments/assets/ac4dc6e8-b099-445d-ab20-bb9347fbbbed" />
<br><br>
<img width="900" height="300" alt="Screenshot from 2025-08-15 17-23-41" src="https://github.com/user-attachments/assets/e68dfca3-f896-4e70-91b4-53f85356bf95" />

---

## ⚙️ Jenkins Setup Steps

### 1️⃣ Install Suggested Plugins
When first launching Jenkins:
- Choose **Install suggested plugins**
- Ensure the following plugins are present (either pre-installed or added manually):
  - Git Plugin
  - Maven Integration Plugin
  - Pipeline Plugin
<img width="700" height="300" alt="Screenshot from 2025-08-15 17-23-56" src="https://github.com/user-attachments/assets/637a6585-6a9d-4ba6-bea5-03ef3b9ba327" />


---

### 2️⃣ Configure Maven in Jenkins
1. Go to: **Manage Jenkins → Tools**
2. Under **Maven Installations**, click **Add Maven**
3. Name it (example: `Maven-jdk`)
4. Select **Install automatically**
5. Choose Maven version (latest available, in our case `3.9.x`)

---

### 3️⃣ Create GitHub Repository
1. Create a new repo in GitHub (example: `hello-java-maven-cicd`)
2. Add your `pom.xml` and Java source files
3. Push the files:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```

### 4️⃣ Configure Jenkins Freestyle Job
1. New Item → Freestyle project
2. Give it a name (example: hello-java-maven)
3. Under Source Code Management:
- Select Git
- Paste your GitHub repo URL
`Example: https://github.com/VisheshGhule/hello-java-maven-cicd`
4. Under Build:
-Choose Invoke top-level Maven targets
-Set Goals to:
```bash
clean package
```
- If pom.xml is in a subdirectory, set POM to the correct path (ours was in root, so just pom.xml)

### Running the Build
- Click Build Now in Jenkins.
- If everything is set correctly, you should see:
```csharp
[INFO] BUILD SUCCESS
Finished: SUCCESS
```
<img width="1000" height="550" alt="Screenshot from 2025-08-15 18-11-44" src="https://github.com/user-attachments/assets/46c357f4-47bf-4eef-99ba-6730a38ba41d" />
