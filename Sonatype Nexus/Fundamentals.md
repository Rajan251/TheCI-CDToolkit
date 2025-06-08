# **Sonatype Nexus: Comprehensive Notes**

## **1. Introduction to Sonatype Nexus**
- **Definition**: Sonatype Nexus is a repository manager that organizes, stores, and distributes software artifacts (binaries, libraries, dependencies).
- **Purpose**: Simplifies dependency management, improves build performance, and ensures secure artifact storage.
- **Types of Repositories**:
  - **Proxy**: Caches remote repositories (e.g., Maven Central).
  - **Hosted**: Stores internally developed artifacts.
  - **Group**: Aggregates multiple repositories into one URL.

## **2. Key Features**
- **Dependency Management**: Resolves and caches dependencies.
- **Security Scanning**: Integrates with tools like Nexus IQ for vulnerability detection.
- **High Availability**: Supports clustering for enterprise use.
- **Multi-Format Support**:
  - Maven (Java)
  - npm (JavaScript)
  - Docker
  - PyPI (Python)
  - NuGet (.NET)
  - Helm (Kubernetes)
  - Raw files
- **Access Control**: Role-based permissions for security.
- **CI/CD Integration**: Works with Jenkins, GitLab CI, etc.

## **3. Core Concepts**
### **3.1. Repository Types**
1. **Proxy Repositories**  
   - Acts as a caching layer for remote repositories.
   - Example: Proxy for Maven Central (`https://repo1.maven.org`).
   
2. **Hosted Repositories**  
   - Stores internal artifacts (e.g., company libraries).
   - Can be **Snapshot** (temporary builds) or **Release** (stable versions).

3. **Group Repositories**  
   - Combines multiple repositories under a single URL.
   - Example: A Maven group repo may include both hosted and proxy repos.

### **3.2. Blob Stores**
- Storage system for binary files (artifacts).
- **Default blob store**: `default` (file system).
- Can use **S3 blob store** for cloud storage.

### **3.3. Components & Assets**
- **Component**: Logical grouping of assets (e.g., a Maven JAR + POM).
- **Asset**: Individual files (e.g., `myapp-1.0.jar`).

### **3.4. Cleanup Policies**
- Automatically removes old/unused artifacts.
- Example: Delete snapshots older than 30 days.

## **4. Security & Access Control**
- **Realms**: Authentication sources (LDAP, SAML, local users).
- **Roles & Privileges**:
  - **Admin**: Full control.
  - **Deployer**: Upload artifacts.
  - **Viewer**: Read-only access.
- **Content Selectors**: Fine-grained access control per repository.

## **5. Nexus IQ Server (Advanced Security)**
- Scans dependencies for vulnerabilities.
- Enforces policies (e.g., block vulnerable libraries).
- Integrates with CI/CD pipelines.

## **6. Installation & Setup**
### **6.1. Installation Methods**
- **Docker**:  
  ```sh
  docker run -d -p 8081:8081 --name nexus sonatype/nexus3
  ```
- **Manual (Java-based)**:
  - Download from [Sonatype](https://www.sonatype.com/products/download).
  - Run `./nexus start` (Linux) or `nexus.exe /run` (Windows).

### **6.2. Initial Configuration**
1. Access `http://localhost:8081`.
2. Default admin credentials: `admin` / `admin123` (change immediately).
3. Set up blob stores, repositories, and user roles.

## **7. Integration with Build Tools**
### **7.1. Maven (`settings.xml`)**
```xml
<servers>
  <server>
    <id>nexus-releases</id>
    <username>deploy-user</username>
    <password>password</password>
  </server>
</servers>
```
### **7.2. npm (`.npmrc`)**
```ini
registry=http://localhost:8081/repository/npm-group/
_auth=base64-encoded-credentials
```
### **7.3. Docker (`daemon.json`)**
```json
{
  "insecure-registries": ["nexus-host:8082"]
}
```

## **8. Best Practices**
- **Regular Backups**: Backup blob stores and databases.
- **Repository Cleanup**: Avoid storage bloat with policies.
- **Security Scanning**: Use Nexus IQ for compliance.
- **High Availability**: Cluster setup for enterprise.

## **9. Troubleshooting**
- **Logs**: Located in `sonatype-work/nexus3/log`.
- **Common Issues**:
  - **403 Forbidden**: Check user permissions.
  - **Storage Full**: Clean up old artifacts.
  - **Slow Performance**: Optimize blob stores (use SSD/S3).

## **10. Alternatives**
- **JFrog Artifactory**
- **Apache Archiva**
- **CloudRepo**

---
### **Summary**
Sonatype Nexus is a powerful repository manager that enhances dependency management, security, and CI/CD workflows. It supports multiple formats, ensures secure artifact storage, and integrates with modern DevOps tools.

