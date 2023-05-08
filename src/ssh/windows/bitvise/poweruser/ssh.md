# Bitvise SSH - Power users

## Open SFTP & Terminal automatically

If you wish, you can have a `Terminal` and `SFTP` window open automatically upon a successful connection. In order to activate this feature, browse to the `Options` tab of Bitvise, and set the `Open Terminal` option to `Always`, and tick the `Open SFTP` checkbox, as shown in the image below. 

<p>
	<center>
		<img src="assets/bitvise_autoopen.png"/>
	</center>
</p>

## SFTP Sync

From the `SFTP` window, you can edit files on the server directly. This is done by right clicking a file of your choice, followed by the `Edit` button. Changes made to the open file will automatically get uploaded to the server, provided the file has proper permissions and is editable by you. 

There is no need to download this file first in order to make changes to it. 

> After making changes to a file, you need to save it in order for the changes to actually get uploaded to the server. 

Please note that this feature only works one way. If someone else opens and changes the file you're editing, you will not see their changes until you re-open the file.

<p>
	<center>
		<img src="assets/bitvise_sync.png"/>
	</center>
</p>

## SFTP Drive Mapping

If you need to have the files accessible locally, as if they were stored on your computer, you can use the `SFTP Drive Mapping` feature of Bitvise, which is accessible from the `Services` tab. Turn on this feature, and tick the `Multi-threaded` checkbox next to it for a boost in performance while operating with files this way. See the image below for more information.

<p>
	<center>
		<img src="assets/bitvise_drive_mapping.png"/>
	</center>
</p>

> You may need to `Log out` from Bitvise if you have a connection open while activating this feature. Upon `Log in`, the feature should work correctly.

After this feature has been activated, you should now be able to see a new `Network drive` in `This PC`, as illustrated below. 

<p>
	<center>
		<img src="assets/bitvise_drive_mapping_mounted.png"/>
	</center>
</p>

> This feature mounts the `SFTP` drive locally, but you'll have to manually navigate to your home folder. If you do not have adequate permissions to list directories along the path to your home directory, you may have to enter the path directly in `Windows Explorer`'s path navigation tab, as illustrated below. 

<p>
	<center>
		<img src="assets/bitvise_drive_path.png"/>
	</center>
</p>