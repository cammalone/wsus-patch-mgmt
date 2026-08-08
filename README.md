<p align="center">
<img width="477" height="187" alt="image" src="https://github.com/user-attachments/assets/370fdd4a-fe3f-4be7-b14c-ffcd77feac47" />
</p>

<h1 align="center">WSUS Patch Management: Deployment, Approval Workflow, and GPO Client Targeting</h1>

<p>This lab demonstrates a complete on-premises patch management workflow using WSUS integrated with the Active Directory environment built in the configure-ad lab. The goal is to show the full lifecycle a systems administrator manages in production: installing and configuring the WSUS role, controlling which update classifications get pulled from Microsoft, structuring computer groups to separate test and production systems, using Group Policy to direct domain clients to the internal WSUS server, and running a staged approval process where updates are validated on a test group before rolling out broadly. It reflects the kind of update governance and risk control expected in real IT infrastructure roles, where patches are never pushed blindly to every machine at once.</p>

<h2>High-Level Deployment and Configuration Steps</h2>
<ol>
  <li>Install the WSUS role the DC.</li>
  <li>Configure WSUS to sync with Microsoft (choosing which products and classifications to pull, excluding driver updates for hardware not present in the lab environment).</li>
  <li>Create computer groups, at minimum a Test group and a Production group, so updates hit one client before the other.</li>
  <li>Point Windows 10 client at WSUS using GPO, so it knows to check the server instead of Microsoft directly.</li>
  <li>Approve updates for Test, confirm they install cleanly, then approve for Production.</li>
</ol>

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (VM hosting for domain controller and client)</li> 
  <li>Remote Desktop Protocol</li> 
  <li>Windows Server 2025 (WSUS role installed on the existing domain controller)</li> 
  <li>Windows 10 (domain-joined client receiving updates)</li> 
  <li>Active Directory Domain Services (existing domain structure from the configure-ad lab)</li> 
  <li>Windows Server Update Services</li> 
  <li>Group Policy Management Console / Group Policy Objects (GPO client targeting and update deployment settings)</li> 
  <li>PowerShell (WSUS configuration and verification commands)</li> 
  <li>Windows Update Agent (client-side component that communicates with WSUS)</li>
</ul>
