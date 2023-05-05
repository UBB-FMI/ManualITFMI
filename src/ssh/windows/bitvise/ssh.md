# Bitvise SSH

## Installing Bitvise SSH

Using a web browser, download the Bitvise SSH installer from [this link](https://dl.bitvise.com/BvSshClient-Inst.exe), which should directly download the appropiate installer. If that doesn't work, try [this link](https://www.bitvise.com/ssh-client-download) instead, which leads to the actual download page of the software. You can see the download button in the image below.

<p>
	<center>
		<img src="assets/download.png"/>
	</center>
</p>

After the installer file has been downloaded, open it. You may be asked for administrative permissions in order to continue, just like in the image below. In this case, allow the modifications. You may be asked to enter your computer's password, if you have one (the one it asks you to enter when you power on your computer).

<p>
	<center>
		<img src="assets/admin.png"/>
	</center>
</p>

After the installer launches, you are asked to accept the software's terms and conditions. In order to proceed, tick the corresponding checkbox and proceed with the installation, as shown in the image below. 

<p>
	<center>
		<img src="assets/installer.png"/>
	</center>
</p>

You may see a black box with files being copied by the installer. This is normal, and represents the way by which the software informs you of what is being done. After this step, you will be prompted to acknowledge the installation, as in the image below. Click OK.

<p>
	<center>
		<img src="assets/installer_ok.png"/>
	</center>
</p>

At this point, the main window of Bitvise SSH should open automatically. If it doesn't, you can find it's icon on the Desktop labelled accordingly.

## Configuring the keypair

> This step only has to be done once, in the beginning. This guide assumes you have not generated keys prior to this, and this the first one that you set up. 

### Generating keys

Click on the "Client key manager" field as indicated below. This will open the key manager interface.

<p>
	<center>
		<img src="assets/bitvise_clientkeymanager.png"/>
	</center>
</p>

In the key generation interface, click on "Generate New", which should bring you to the next step. Consult the image below. 

<p>
	<center>
		<img src="assets/bitvise_generatekey.png"/>
	</center>
</p>

In the newly opened window, you are asked about setting a passphrase to your keypair. If you decide you need one, please enter the same passphrase in fields `1` and `2`, then proceed to generating your keypair by clicking `Generate`, on step `3`. See the image below for more instructions.

> This step is optional, but **highly recommended**. A keypair without a passphrase allows for passwordless login, but at the same time, in the event that the key gets stolen, the thief can also log into your account without the need for a password. It is up to you to decide how you want it, but it is also your responsability of taking care of your account. 

<p>
	<center>
		<img src="assets/bitvise_keypassphrase.png"/>
	</center>
</p>

Congratiulations! Your keypair has now been generated. Please proceed to see details on how to install these keys on the server(s).

### Installing the public key

Once you have genertaed 

bitvise_pubkey.png