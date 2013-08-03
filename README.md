Decrypt_Encrypt
===============

This script uses 2 EXECUTE commands to open (decrypt) an encrypted data container (volume, which can be a file, partition, or device), process the data files in that volume, then close (encrypt) the data when done. This will protect sensitive data while not in use during the project. If multiple users have ACL projects that must access the same sensitive data file, one copy of the data file in an encrypted container would be safer than multiple local copies of unencrypted data. The encryption software used is TrueCrypt (open source, free) http://www.truecrypt.org/ 

Authenication is accomplished using a key file for a "what you have" factor. Maybe the next version of Analytics we can use the PASSWORD command within the EXECUTE command.

See the TrueCrypt documentation steps for creating the volume and specifying key file authentication. Ensure the storage location of the key file is limited to those authorized to access the encrypted data.

The ASSIGN commands at the front determine the location of the encrypted volume, the location of and name of the key file for authentication and the drive letter assigned to the decrypted volumn. Other items such as which file is Imported are more hard coded but also could be made dynamic with variables based on your situation.

An alternative would be to place the ACL project inside the encrypted volume along side the data, then you would not need the EXECUTE commands within the script, but would would have to authenticate and access the volume before starting your ACL project.

WARNING: If you are running the ACL project outside of the encrypted volume, the local ACL log file is NOT encrypted, be careful with TO SCREEN output options because some commands such as DUPLICATES may place sensitve data in the unencrypted log. Also, if IMPORT, EXTRACT or EXPORT commands are used in your script, ensure the .FIL and other file format's contents are sent to an appropraite encrypted volume if required.




