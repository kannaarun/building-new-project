# building-new-project
pool:
  name: "Azure Pipelines"
  vmImage: ubuntu-22.04

trigger:
  - master

steps:
  - task: DotNetCoreCLI@2
    inputs:
      command: build
      projects: src/NopCommerce.sln
