# Microsoft Sentinel Operations Dashboard (lab)

A personal lab project: set up Microsoft Sentinel, connect data sources, and build up detection and monitoring content, documenting each step.

This lab runs in my own Azure free-trial subscription. It is a learning project, not a production or client environment.

## Environment
- Region: East US
- Log Analytics workspace: law-sentinel-lab
- Resource group: rg-sentinel-lab
- Started: 18 October 2026

## What I built so far
- Created a resource group and Log Analytics workspace
- Added Microsoft Sentinel to the workspace (31-day free trial)
- Registered the resource providers Sentinel needs
- Assigned the Azure Policy that sends Azure Activity logs to the workspace, with a system-assigned managed identity
- Set a monthly cost budget with email alerts

## In progress
- Confirming Azure Activity data arrives (KQL: AzureActivity | take 10)
- Microsoft Entra ID connector
- Analytics rules and a workbook (dashboard)

## Troubleshooting log
Problems I hit and how I fixed them:

1. Adding Sentinel to the workspace failed. Cause: the resource providers Microsoft.SecurityInsights and Microsoft.OperationalInsights were not registered on the new subscription. Fix: registered both under Subscriptions > Resource providers.
2. Policy assignment for the Azure Activity connector failed. Cause: the policy needs a managed identity because it deploys settings. Fix: used a system-assigned managed identity with the suggested roles.
3. The remediation task failed. Cause: Microsoft.PolicyInsights was not registered. Fix: registered it and re-ran the remediation.
4. KQL gave a syntax error. Cause: only line 2 was highlighted, so Run executed just that part. Fix: deselected the text before running.

## Notes
- Screenshots have IDs, emails and tenant names removed.
- Trial credit and the Sentinel free trial end in November 2026, so the resources will be deleted afterwards and the code and notes kept here.
