# GO to the directory where are the files
cd Ansible

# Copie list of encrypted files
mv encrypted ../

# Decrypt files
for myfile in `cat ../encrypted`; do echo $myfile; gpg  --pinentry-mode=loopback --passphrase  "MON_MOT_DE_PASSE" --batch --yes --decrypt "$myfile.gpg" >> $myfile; done;

# Delete Encrypted files
find . -type f -not -path '*/.git/*' -not -name 'encrypted' -name '*.gpg' -delete
