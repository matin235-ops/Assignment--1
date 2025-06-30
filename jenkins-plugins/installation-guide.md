# Jenkins Plugin Installation Guide

## Required Plugins for DevOps Integration

### 1. Jira Plugin
**Installation:**
1. Go to Jenkins Dashboard
2. Navigate to "Manage Jenkins" > "Plugin Manager"
3. Click on "Available" tab
4. Search for "Jira"
5. Select "Jira" plugin
6. Click "Install without restart"

**Configuration:**
1. Go to "Manage Jenkins" > "System Configuration"
2. Find "Jira Steps" section
3. Add Jira Site:
   - Name: Your Jira Project Name
   - URL: Your Jira Cloud URL (e.g., https://yourcompany.atlassian.net)
   - Credentials: Add your Jira email and API token

### 2. GitHub Plugin
**Installation:**
1. Go to "Manage Jenkins" > "Plugin Manager"
2. Search for "GitHub"
3. Install "GitHub" plugin
4. Install "GitHub Branch Source" plugin

**Configuration:**
1. Already configured with webhook integration

### 3. Performance Plugin (for JMeter)
**Installation:**
1. Go to "Manage Jenkins" > "Plugin Manager"
2. Search for "Performance"
3. Install "Performance" plugin

**Configuration:**
1. No additional configuration needed
2. Use in pipeline with publishTestResults step

### 4. Docker Plugin
**Installation:**
1. Go to "Manage Jenkins" > "Plugin Manager"
2. Search for "Docker"
3. Install "Docker" plugin
4. Install "Docker Pipeline" plugin

**Configuration:**
1. Go to "Manage Jenkins" > "System Configuration"
2. Find "Docker" section
3. Add Docker Host URI if needed (usually auto-detected)

## Post-Installation Steps
1. Restart Jenkins if required
2. Verify all plugins are active in "Installed" tab
3. Configure each plugin according to the above instructions
