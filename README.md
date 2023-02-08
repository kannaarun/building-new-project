# building-new-project
pool: Default

trigger:
  - master

jobs:
  - job: Build_Job
    displayName: Build dotnet project
    steps:
      - task: DotNetCoreCLI@2
        inputs:
          command: 'build'
          projects: src/dotnet-demoapp.csproj
  - job: Test_Job
    displayName: Test dotnet
    dependsOn: Build_Job
    condition: succeeded()
    steps:
      - task: DotNetCoreCLI@2
        inputs:
          command: 'build'
          projects: tests/tests.csproj
