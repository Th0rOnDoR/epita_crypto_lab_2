> ![NOTE] cat `secret.age.` How many times is the payload encrypted? What is duplicated per recipient? What exactly is in each recipient block? (You built the same thing by hand in Lab 1.)

3 times, one per person.


> ![NOTE] The file is deleted in HEAD. If you would have pushed, Who can still read the password?

The ones using a previous version

> ![NOTE] After filter-repo, is the password safe? What did you have to do first?

Might not be, we purged the local only, and we can't purge a remote.

> ![NOTE] What does git commit --no-verify do to your hook? Where else must the same check run?

It allows to commit without running the git hooks.
Checks must be run in cicd pipelines.

> ![NOTE] Decrypt prod with bob.key: what happens? Edit one encrypted value by hand: what does sops say?

thorondor[11:27:21]:/tmp/epita_crypto_lab_2 $ SOPS_AGE_KEY_FILE=bob.key sops -d secrets/prod/database.yaml
Failed to get the data key required to decrypt the SOPS file.

Group 0: FAILED
  age1kg8u9nppgr4r3nea39gegr56ar8fwnwaxp0yasw08mcrf6tpz50s9fypz3: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: no identity matched any of the recipients. Did not find
      | keys in locations 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

  age1aw846qyyf5dzhglk7xazz775x27wl2d8q09p02kx3hv5hrh73u6qxysq6p: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: no identity matched any of the recipients. Did not find
      | keys in locations 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

Recovery failed because no master key was able to decrypt the file. In
order for SOPS to recover the file, at least one key has to be successful,
but none were.

Failed to get the data key required to decrypt the SOPS file.

Group 0: FAILED
  age1kg8u9nppgr4r3nea39gegr56ar8fwnwaxp0yasw08mcrf6tpz50s9fypz3: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: failed to read header: failed to parse header: failed
      | to read line: invalid armor: illegal base64 data at input
      | byte 60. Did not find keys in locations
      | 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

  age1aw846qyyf5dzhglk7xazz775x27wl2d8q09p02kx3hv5hrh73u6qxysq6p: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: no identity matched any of the recipients. Did not find
      | keys in locations 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

Recovery failed because no master key was able to decrypt the file. In
order for SOPS to recover the file, at least one key has to be successful,
but none were.

-- Manual Edit

thorondor[11:28:12]:/tmp/epita_crypto_lab_2 $ sops -d secrets/prod/database.yaml
Failed to get the data key required to decrypt the SOPS file.

Group 0: FAILED
  age1kg8u9nppgr4r3nea39gegr56ar8fwnwaxp0yasw08mcrf6tpz50s9fypz3: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: failed to read header: failed to parse header: failed
      | to read line: invalid armor: illegal base64 data at input
      | byte 60. Did not find keys in locations
      | 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

  age1aw846qyyf5dzhglk7xazz775x27wl2d8q09p02kx3hv5hrh73u6qxysq6p: FAILED
    - | failed to create reader for decrypting sops data key with
      | age: no identity matched any of the recipients. Did not find
      | keys in locations 'SOPS_AGE_SSH_PRIVATE_KEY_FILE',
      | 'SOPS_AGE_SSH_PRIVATE_KEY_CMD',
      | '/home/thorondor/.ssh/id_ed25519', 'SOPS_AGE_KEY', and
      | 'SOPS_AGE_KEY_CMD'.

Recovery failed because no master key was able to decrypt the file. In
order for SOPS to recover the file, at least one key has to be successful,
but none were.

