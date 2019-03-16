Accessing The Atmosphere Cloud
===

![](/img/setup1.png)

- **Atmosphere, CyVerse's cloud-computing platform allows you to launch your own isolated virtual machine (VM) image and software, using compute resources such as CyVerse-provided software suites, and pre-configured, frequently used analysis routines, relevant algorithms, and datasets.**

> To request access to Atmosphere, login to the [CyVerse User Portal](https://user.cyverse.org/). In the [Services](https://user.cyverse.org/services/mine>) menu under 'MY SERVICES' you should see Atmosphere listed as an option you can launch. If not, look uner the [Available](https://user.cyverse.org/services/available) menu, and click the 'REQUEST ACCESS' link. You will receive an email requesting additional information.

- This is the first and last place in these lessons where it will matter if you are using PC, Mac, or Linux. After we connect to our virtual machines built using the same image; we will all be on the same operating system/computing environment.

- Documentation on how to use Atmosphere resources can be found [here](https://learning.cyverse.org/projects/atmosphere-guide/en/latest/index.html)

### SSH Client for WINDOWS users

- Windows-users will need to install UNIX-ready terminal.

- Download & Install [mobaxterm home edition](http://mobaxterm.mobatek.net/download-home-edition.html)

- Start a new session; Fill in your "remote host" the IP address of your virtual machine. Then select "specify username" and enter your cyverse username; Click OK.

# Login & Launch Instance

- Login to [Atmosphere](https://atmo.cyverse.org/application/images) by clicking the "login" butoon (right-upper corner).

![](/img/login1.png)

- Fill in your CyVerse username and password and click "LOGIN"

![](/img/login2.png)

- Select the "Projects" tab and then click the "CREATE NEW PROJECT" button

![](/img/login3.png)
![](/img/login4.png)

- Give your Project folder a name (Description is optional). Then click "CREATE".

![](/img/login5.png)

- Click on your newly created project.

- Click "NEW" and then "Instance" from the dropdown menu to start up a new virtual machine.

![](/img/login6.png)

- To select an image click on **"Show All"** tab and Search for **"DCG-UNR-RNAseq"** and choose the "DCG-UNR-RNAseq" image created by 'sateeshp'.

![](/img/login7.png)

- Basic options
	+ Instance Name: e.x., "workshop" or you can leave it default which is the image name.

	+	Base Image Version: "3.0"

	+	Project: select project folder to host the instance

	+	Allocation Source: should be your cyverse account

	+	Provider: "CyVerse Cloud - Marana"

	+ Instance size: **Depending on your allocations, choose most suitable one.**
  	+ Recommended for this tutorial: "tiny1 (CPU: 1, Mem: 4GB, Disk: 30GB)"

![](/img/login8.png)

- Launch instance and wait for the build to be deployed.

- The virtual machine should now be booting up! and should take ~ 5-10 minutes. **Note: During the build process..Be patient! Don't reload or do anything. Once the virtual machine is ready, the "Activity" column will show "N/A" and the "Status" column will turn green and "Active" (see below)**

![](/img/login9.png)

- Navigate back to 'Projects' and click on your new instance's name to see more information related to the instance you just created!

- Copy the IP address of your instance.

![](/img/login10.png)

# SSH Secure-Login

- MACOS & LINUX users can open a Terminal window and Windows users start a new session in mobaxterm (see # Setup)

- Establish a secure-login to the instance by typing the following:

```
ssh your_cyverseusername@ip_address
```
- This should log you into CyVerse and you should see a screen like this:

![](/img/ssh1.png)

- Enter 'yes' and then you will be asked for your CyVerse password.

> Your cursor will not move or indicate you are typing as you enter your password. If you make a mistake, hit enter and you will be prompted again.

- Successful login should look something like below 

![](/img/ssh2.png)

> To close your current session and end SSH connection, type 'exit'

![](/img/ssh3.png) 

# Instance Maintenance

#### Atmosphere Dashboard

![](/img/maintain1.png)

#### Delete Instance

- To completely remove your instance, you can select the "Delete" button from the instance details page.

- This will open up a dialogue window. Select the "Yes, delete this instance" button.

- It may take Atmosphere a few minutes to process your request. The instance should disappear from the project when it has been successfully deleted.

![](/img/maintain3.png)

#### Suspend Instance

![](/img/maintain2.png)

**Note: It is advisable to delete the machine if you are not planning to use it in future to save valuable resources. However if you want to use it in future, you can suspend it. Notice: IP address changes**

#### Request More Allocation Units

![](/img/maintain4.png)


# Additional Features

#### Web Shell

- Access Command-Line Directly from your browser

![](/img/additional1.png)

#### Web Desktop

- Access your instance through a web desktop version from your browser

![](/img/additional2.png)

#### Transferring Data to and from an Instance

An Atmosphere instance only contains data that were included in the original image that was used to make that instance. You can transfer data to/from the CyVerse Data Store, an Atmosphere Volume, a sever, or your local machine. In this guide, we will only cover data transfer using iCommands. iCommands is installed on every Atmosphere instance.


> **Related Links**

- [**iCommands Guide:**](https://cyverse-data-store-guide.readthedocs-hosted.com/en/latest/step2.html)
- [**iCommands Download:**](https://wiki.cyverse.org/wiki/display/DS/Setting+Up+iCommands)


**Transferring Data to/from an Instance using iCommands**

You can execute to the instance's icommand if you are connected via SSH or if you are connected to the desktop via VNC, open the instance's terminal application.


  1. At the instance's terminal, start the iCommands configuration using the
     'iinit' command and enter configure.

      .. important::
          This configuration is a one-time step on your first use with this
          instance.

        .. code:: bash

          $ iinit

          # As prompted, enter the following values:
          # Host: data.cyverse.org
          # Port: 1247
          # User: your_cyverse_username
          # Zone: iplant
          # Password: your_cyverse_password

        If you make a mistake in your configuration you can edit `~/.irods/irods_environment.json`
        on your instance.

  2. Test your configuration by listing your Data Store contents with the "ils"
     command.

      .. code:: bash

        $ ils

      .. Tip::
          If you made a mistake during the configuration, you can edit your
          icommands configuration file.

  3. To download a file from the Data Store to your instance, use "iget"

      .. code:: bash

        $iget data_store_file

  4. To upload file from your instance to the Data Store use "iput"

      .. code:: bash

        $iget file_on_instance location_on_data_store


.. tip::
    iCommands has a variety of options, to see progress of transfers, operate
    recursively, and more. See additional [iCommands documentation](https://wiki.cyverse.org/wiki/display/DS/Using+iCommands) on the CyVerse wiki.

===

#### Custom Images

- [Jetstream](https://hackmd.io/im0eDxViQgmxTL4zYBfGoQ#)

#### Deposit rsa-key

-	Concerning Keys: 
	Cryptographic keys are a convenient and secure way to authenticate without having to use passwords. They consist of a pair of files called the public and private keys: the public part can be shared with whoever you’d like to authenticate with (in our case, CyVerse Atmosphere!), and the private part is kept “secret” on your machine. Things that are encrypted with the public key can be be decrypted with the private key, but it is computationally intractable (ie, it would take on the order of thousands of years) to determine a private key from a public key. You can read more about it [here](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)

- Create the RSA Key Pair on your laptop/computer:

```
$ ssh-keygen -t rsa
```

- Store the Keys and Passphrase. Once you have entered the Gen Key command, you will get a few more questions:

```
$ Enter file in which to save the key (/home/demo/.ssh/id_rsa):
```

- You can press enter here, saving the file to the user home (in this case, my example user is called demo).

```
$ Enter passphrase (empty for no passphrase):
```

- It's up to you whether you want to use a passphrase though we recommend NOT to!.

- The public key is now located in /home/demo/.ssh/id_rsa.pub. The private key (identification) is now located in /home/demo/.ssh/id_rsa

- Copy the Public Key

- Once the key pair is generated, it's time to place the public key on the server that we want to use.

```
$ cat ~/.ssh/id_rsa.pub
```

- Copy all of the text that constitutes your public key and we will place it in our Atmosphere accounts.

- **Deposit key on Atmosphere**

- You are now ready to deposit your generated public key onto your Atmosphere account, to gain secure login each time you build and use an instance on Atmosphere.

- Click on your username on the Atmosphere page and navigate to 'Settings' page

![](/img/additional3.png)

- Scroll down to the advanced section and click on 'Show More'

![](/img/additional4.png)

- In the 'SSH Configuration' section, click on the '+' sign 

![](/img/additional5.png)

- Paste your public key generated earlier and give this key a name

![](/img/additional6.png)

- **You can now securely login to all the instances you launch on Atmosphere without having to type your password each-time you ssh login.**