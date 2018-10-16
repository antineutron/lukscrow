
LUKScrow - automatic Active Directory recovery key escrow for LUKS full disk encryption

The general idea is to provide a way to generate a recovery key for the root volume
which is then stored in Active Directory and accessible by administrators in case
of emergency e.g. the laptop user forgot their passphrase. In theory this should
also work against FreeIPA or an LDAP server with Kerberos authentication, but this
has not been tested.

There is also an option to remove the initial unlock key - this is useful for
automated installations, in which a default key (potentially known to many people)
is used for the initial disk encryption, then the random recovery key is
generated and the original key deleted (note that you'd probably want to
get the laptop's owner to manually add their own key first!)

Currently left as an exercise to the reader: automated unlocking using the TPM

Assumptions:
* The target LUKS device has already been set up with a passphrase
* The machine has already been joined to the Active Directory domain and has a valid keytab

Currently a bit rough around the edges especially with error reporting!

