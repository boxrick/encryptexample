Vault password with GPG example, to encrypt a single key with multiple users

# Create vault password with gpg public keys
echo 'BbIrJxvNPjmo7XDcnoB2ixw0tMN5Znd3ZVv7zF3lhx2Fd41OpC' | gpg --batch --yes --output ./vault-password.gpg --encrypt --recipient F2FE69773D8366F41A7EB27A5DD30497D993AC57 --recipient 40BCED53CD6E3608C180844286D5DC86A00B95C6 --recipient 075BB1F00EF3031449924C2848F3C9AFE941AEC9 --recipient B508BF4B20A9E10A33FB66B63D797148B85C5AC3

# Create vault data with above password, if vault password file is defined in ansible.cfg it will make use of this instead of asking for a new password
# vault_password_file=pull_vault_password.sh

echo 'supersecretpassword' | ansible-vault encrypt_string --stdin-name 'encrypted_blob'
# Place output into variables file
#encrypted_blob: !vault |
          $ANSIBLE_VAULT;1.1;AES256
          37383235366661383365336130303231366465343166363164383436323634386365623463373963
          6638653664633763613933313733323136636338393865390a343964343261626530343534616463
          32346363336532666638626662636165353234626232313266393261616431383063343965333235
          6332623934363761310a363039613364633433663465343733663866333033366333393939373535
          63346537633366396536373939306634343633356131376334303661633837306530
