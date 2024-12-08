<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

<h1>Deploying On-Premises Active Directory in the Cloud (Azure)</h1>
In this home lab, I’ll set up a Domain Controller (DC) and a Client VM in Azure. After creating the necessary network resources, I’ll deploy "DC-1" with a static IP and disable its firewall. Then, I’ll create "Client-1," set its DNS to DC-1’s IP, and verify connectivity by pinging DC-1 and checking DNS settings.

<h2>Environments and Technologies Used</h2>
<ul>
  <li>Microsoft Azure (Virtual Machines/Compute)</li>
  <li>Remote Desktop</li>
  <li>Active Directory Domain Services</li>
  <li>PowerShell</li>
</ul>

<h2>Operating Systems Used</h2>
<ul>
  <li>Windows Server 2022</li>
  <li>Windows 10 (21H2)</li>
</ul>

<h2>High-Level Deployment and Configuration Steps</h2>

<h3>Setting Up the Domain Controller in Azure</h3>
<ol>
  <li>Create a Resource Group</li>
  <li>Create a Virtual Network and Subnet</li>
  <li>Create the Domain Controller VM (Windows Server 2022) named <code>DC-1</code></li>
  <ul>
    <li>Username: <code>labuser</code></li>
    <li>Password: <code>Cyberlab123!</code></li>
  </ul>
  <li>After the VM is created, configure the Domain Controller’s NIC Private IP address to be static</li>
  <li>Log into the VM and disable the Windows Firewall (for testing connectivity)</li>
</ol>
<p align="center">
  <img src="https://github.com/user-attachments/assets/92697741-60f8-439d-9c74-1cc8fd16f916" alt="Domain Controller VM Screenshot" />
</p>

<h3>Setting Up Client-1 in Azure</h3>
<ol>
  <li>Create the Client VM (Windows 10) named <code>Client-1</code></li>
  <ul>
    <li>Username: <code>labuser</code></li>
    <li>Password: <code>Cyberlab123!</code></li>
  </ul>
  <li>Attach Client-1 to the same region and Virtual Network as DC-1</li>
  <li>After the VM is created, configure Client-1’s DNS settings to use DC-1’s Private IP address</li>
</ol>
<p align="center">
  <img src="https://github.com/user-attachments/assets/830525e9-dfdd-4f3a-9793-740b4698779b" alt="Client-1 VM Screenshot" />
</p>

<h3>Testing Connectivity</h3>
<ol>
  <li>From the Azure Portal, restart Client-1</li>
  <li>Login to Client-1</li>
  <li>Attempt to ping DC-1’s private IP address</li>
  <ul>
    <li>Ensure the ping succeeds</li>
  </ul>
  <li>From Client-1, open PowerShell and run <code>ipconfig /all</code></li>
  <ul>
    <li>Ensure the DNS settings show DC-1’s private IP address</li>
  </ul>
</ol>
<p align="center">
  <img src="https://github.com/user-attachments/assets/492b953e-6841-4d60-a19d-b5cbeab62683" alt="PowerShell Output Screenshot" />
</p>

# Key Takeaways: Deploying On-Premises Active Directory in Azure

- **Azure Resource Setup**: Creating a Resource Group, Virtual Network, and Subnet to host the infrastructure.
- **Domain Controller Setup**: Deployed a Windows Server 2022 VM (`DC-1`) as a Domain Controller in Azure.
- **DNS Configuration**: Configured the DNS settings of Client-1 to point to the Domain Controller's static IP.
- **Firewall and Connectivity Testing**: Disabled Windows Firewall on the Domain Controller for initial testing and verified connectivity using `ping` and `ipconfig /all`.
- **PowerShell Verification**: Used PowerShell to confirm DNS resolution between the Domain Controller and Client VM.
