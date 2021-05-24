**Build vs Release Pipelines**

**Build:**
- Builds solution (Example: .Net function apps using vsbuild)
- Runs tests
- Creates an artifact

**Release:**
- Config injection in release pipelines
- Deploy to environment

**Config Management**
Variable Groups
1 variable group per env per region

**Pipeline Arch**
- 1 pipeline per component per life cycle (Dev, UAT, Prod)
- Manual triggers for Release Pipelines
- Automated triggers for Build Pipelines
