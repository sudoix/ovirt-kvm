# Installation and Configuration of oVirt Engine on Oracle linux 8.10

To deploy Oracle Linux Virtualization Manager, you install and configure the
engine on a host with Oracle Linux 8.8 (or later Oracle Linux 8 release),
configure KVM hosts, storage, and networks, and create virtual machines.

#### Installing the Engine

```
# dnf install oracle-ovirt-release-45-el8
```
Install the Manager using the ovirt-engine command.

```
# dnf install ovirt-engine
```
#### Configuring the Engine

After you install the Oracle Linux Virtualization Manager, you run the `engine-setup`
command (the Setup program) to configure the Manager. 
You are prompted to answer a series of questions whose values are used to configure the Manager.
Some of these questions relate to features that are in technology preview.

##### Restart the server

#### Logging in

You log in to the Administration Portal using a web browser and the default admin@internal user.

Go to https://manager-fqdn/ovirt-engine. The Welcome page displays.

(Optional) Change the preferred language from the drop-down list on the Welcome page.

You can view the Administration Portal in multiple languages. The default language is based on the locale of your web browser.

Click Administration Portal. The Login page displays.

Enter admin for the Username and the password you specified when you configured the Manager.

From the Profile list, select internal and click Log In.

###### DONT FORGET: The user name are something like admin@ovirt, admin@internal, etc.


# Configuring a KVM Host

## Preparing a KVM Host

Before you can add an Oracle Linux KVM host, prepare it by performing a fresh \
installation of Oracle Linux 8.8 (or later Oracle Linux 8 release) and enabling the required repositories. 

```
# dnf install oracle-ovirt-release-45-el8
```
### Adding a KVM Host

To add an Oracle Linux KVM host:

Log in to the Administration Portal.

See Logging in to the Administration Portal for details.

Go to Compute and then click Hosts.

On the Hosts pane, click New.

The New Host dialog box opens with the General tab selected on the sidebar.

From the Host Cluster drop-down list, select the data center and host cluster for the host.

The Default data center is auto-selected.

When you install Oracle Linux Virtualization Manager, a data center and cluster named Default is created. You can rename and configure this data center and cluster, or you can add new data centers and clusters, to meet your needs. See the Data Centers or Clusters tasks in the Oracle Linux Virtualization Manager: Administration Guide.

In the Name field, enter a name for the host.

In the Hostname field, enter the fully-qualified domain name or IP address of the host.

In the SSH Port field, change the standard SSH port 22 if the SSH server on the host uses a different port.

Under Authentication, select the authentication method to use.

Oracle recommends that you select SSH PublicKey authentication. If you select this option, copy the key displayed in the SSH PublicKey field to the /root/.ssh/authorized_keys file on the host.

Otherwise, enter the root user's password to use password authentication.

(Optional) Configure other settings for the host from the other tabs on the New Host sidebar.

Note:If you do not want to set any other configuration options now, you can always make changes later by selecting a host from the Hosts pane and clicking Edit.
Click OK.

The Power Management Configuration screen is displayed.

If you do not want to configure power management, click OK. Otherwise, click Configure Power Management.
