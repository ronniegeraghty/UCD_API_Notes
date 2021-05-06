# Deployment Request ID -> Full Trace With Logs
***Purpose**: Go from the Deployment Request ID, given by the UCD Jenkins Plugin, to downloading a zip of all deployment step output logs.*<br/>
***Note:** To use any of the UCD REST APIs you will need to setup authentication. You can learn about the different authentication methods for the UCD Server API here: [UCD REST API Authentication](https://www.ibm.com/docs/en/urbancode-deploy/7.1.2?topic=reference-authenticating-rest-commands)*

- `{{host}}` = UCD Server Hostname
- `{{port}}` = UCD Server Port

## Step 1: Get Deployment Process Trace ID 
- ```https://{{host}}:{{port}}/rest/deploy/applicationProcessRequest/<id>```
  - `<id>` = Deployment Request ID from Jenkins Console Output
  - **Response:** *Type: Object*
    - `.traceId: string`

## Step 2: Download all Deployment Output Logs
- ```https://{{host}}:{{port}}/rest/workflow/<traceId>/fullTraceWithLogs```
  - `<traceId>` = Trace ID from prev step
  - **Response:** Downloaded zip with all deployment step's stdOut.txt logs. 

---

> Ronald Geraghty<br/>
> ronald.geraghty@ibm.com<br/>
> May 5th, 2021