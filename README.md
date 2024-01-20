# windows-networking-lab
Simple way to connect a windows server 2019 and other VM in VirtualBox

# Mini Network Lab Setup with Windows Server and Windows 10 in VirtualBox

Creating a simple network lab within VirtualBox using Windows Server and Windows 10 can be a great way to learn about networking. This guide is designed to be clear and straightforward, suitable for beginners.

## Prerequisites

- Download the [Windows Server 2019 ISO](#).
- Download the [Windows 10 ISO](#).

## Step 1: Install VirtualBox

Download and install [Oracle VM VirtualBox](https://www.virtualbox.org/) on your host machine.

## Step 2: Install the Operating Systems

Create two new virtual machines (VMs) in VirtualBox and install Windows Server 2019 on the first VM and Windows 10 on the second VM.

## Step 3: Configure VirtualBox Network

1. Open VirtualBox, go to `File > Preferences > Network`.
2. Click on the "NAT Networks" tab and then on the "Add new NAT Network" button.
3. Optionally change the name of the NAT Network.
4. Take note of the "IPv4 Prefix" under General Options for later use.

## Step 4: Configure Windows Server Network Settings

1. Start your Windows Server VM and open Server Manager.
2. Click on "Local Server".
3. Click on the "Ethernet" link to open network settings.
4. Right-click your network adapter and choose "Properties".
5. Select "Internet Protocol Version 4 (TCP/IPv4)" and click "Properties".
6. Configure your static IP, subnet mask, default gateway, and DNS.

    ```plaintext
    IP address: 10.0.2.10
    Subnet mask: 255.255.255.0
    Default gateway: 10.0.2.1
    Preferred DNS server: 8.8.8.8
    ```

## Step 5: Configure Windows 10 Network Settings

Repeat similar steps on your Windows 10 VM, ensuring the IP address is unique within the network.

## Step 6: Verify Connectivity

1. Use the `ping` command to test connectivity to the default gateway and the internet.
2. Test the connectivity between your Windows Server and Windows 10 VMs.

    ```cmd
    ping 10.0.2.1
    ping 8.8.8.8
    ```

## Step 7: Enable ICMP on Windows Server

Allow ICMP (ping requests) through the Windows Server firewall with the following PowerShell command:

    ```powershell
    New-NetFirewallRule -DisplayName "Allow ICMPv4-In" -Protocol ICMPv4 -IcmpType 8 -Enabled True -Action Allow -Profile Any
    ```

## Step 8: Test Lab Functionality

Try accessing the internet from both VMs and sharing files between them to validate your network lab setup.

## Conclusion

You've successfully set up a basic network lab with Windows Server and a Windows 10 VM in VirtualBox. You can expand this lab by adding more VMs or exploring other networking features.

