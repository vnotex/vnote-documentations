# Encrypted Notes

VNote can encrypt the **body** of individual **Markdown**, **plain-text**, and **mind-map** notes in a writable **bundled notebook**. Raw notebooks do not support this feature. Encrypted notes use a password-protected, portable key hierarchy; ordinary notes in the same notebook remain unencrypted.

!!! warning "Body encryption is not whole-notebook encryption"
    Filenames, folder names, tags, and other notebook metadata remain visible. Images and attachments stored as separate files, and comment sidecar files, remain **unencrypted**. Encryption does not erase plaintext already present in Git history, cloud versions, backups, shared resources, or external source files. It is not secure deletion.

## Create or encrypt a note

- For a new note, choose a supported type in **New Note** and check **Encrypt note**.
- For existing notes, select them in the notebook explorer and choose **Encrypt** from the context menu. Select notes from one notebook at a time, review the warning, and confirm **Encrypt**. VNote converts the selected note bodies in place; it does not scan or rewrite their separate assets.

On first use, VNote prepares the notebook's encryption keys:

1. If no available initialized notebook supplies a master password, **Set Up Note Encryption** asks for **Master password** and **Confirm password**. Enter matching values and choose **Set Up Encryption**.
2. If another open bundled notebook already has encryption initialized, VNote uses that notebook's master-password hierarchy, asking you to unlock it if necessary. If several different hierarchies are available, **Choose Master Password** lets you select the source notebook.
3. Once this notebook is initialized, subsequent operations unlock its existing keys rather than creating new ones.

!!! danger "Keep the master password"
    Forgotten master passwords cannot be reset to recover encrypted contents. Keep the password safe and back up the complete notebook, including its keys. A sync password or Personal Access Token does not unlock encrypted notes.

### Older notebooks and first-time setup

An older notebook may have no recorded encryption-initialization state. If `vx_notebook/encryption.vne` is absent and previous encryption use is unknown, VNote asks for explicit confirmation before setup. Continue **only if this notebook has never used encryption**. Cancelling that confirmation leaves notes and configuration unchanged.

If it has used encryption before, cancel and restore the original key data from a complete, consistent backup. A newly generated key cannot recover notes encrypted with a missing key. See [Backup and recovery](#backup-and-recovery).

## Unlock and lock

Open an encrypted note in VNote and enter the master password when prompted. Unlocking makes the protected body available to its VNote editor; it does not turn the on-disk note into an ordinary plaintext file. Opening protected notes with an external application is not supported.

Use **Settings menu → Lock All** to save protected edits and close protected views while leaving ordinary note tabs open. If saving or locking reports an error, resolve it rather than assuming the notebook is locked.

## Decrypt in place

Select encrypted notes in the notebook explorer and choose **Decrypt**. Unlock if requested, review the warning, and confirm **Decrypt** to return them to normal notes in place. This is a conversion, not an export or a separate plaintext copy.

The note body, including embedded Base64 images, will then be stored **unencrypted**, and future syncs or backups may include that plaintext. Separate images, attachments, and comments are unchanged; previous history and backups are not erased by decryption either.

## Images, previews, search, and export

- **Embedded images:** Base64 is the default image insertion method for encrypted Markdown notes. Base64 is encoding, not encryption: image bytes are protected only when they are saved inside the encrypted body. Previously linked image files are not automatically embedded or encrypted. See [Images & Image Host](../editing/images-and-image-host.md) for insertion choices.
- **Separate resources:** attachment actions such as **Open**, **Open Folder**, and **Copy Path** still operate on ordinary unencrypted files. Do not put secrets in separate attachments or comments expecting body encryption to protect them.
- **Previews and math:** protected previews use memory-only profiles. Bundled KaTeX works offline in encrypted Markdown read mode and live preview; in-place math previews remain unavailable. See [Math & Diagrams](../editing/math-and-diagrams.md).
- **Search:** ordinary cross-note content search skips encrypted note bodies, **even when a note is unlocked**. Search can report the number of encrypted files skipped; visible names, folders, and tags remain available for finding notes. Unlocking does not opt a body into global search or replacement. See the [Search Panel](../search/search-panel.md).
- **Export and print:** exporting or printing encrypted note bodies is not supported. See [Export](../productivity/export.md) for ordinary notes; decrypting first deliberately removes the body's encryption protection.

## Backup and recovery

Copy or synchronize the **entire notebook**, including its configuration and complete key hierarchy, and retain the master password. A lone encrypted note file is not a sufficient backup. If you use custom external asset or recycle-bin paths, include those separately as described in [Notebook Sync](notebook-sync.md).

If VNote reports that a known encryption key is missing or needs recovery, preserve the current notebook and backups, and restore its original `vx_notebook/encryption.vne` and matching notebook data from a consistent backup. **Do not delete key files, replace them with newly generated keys, or mix encrypted files and keys from different versions.** If a conversion or creation error requests a restart before editing or syncing, follow that instruction before continuing; preserve recovery data if the error persists.

For transferring selected notes, use VNote's [cross-notebook copy/move](notebooks-folders-notes.md#copy-and-move-between-notebooks) or [shared-folder import](importing-migrating.md#import-a-shared-folder), not a manual copy of isolated encrypted files. An encrypted shared-folder import needs the source master password and an initialized, unlocked destination notebook; its full workflow is covered in the import guide.
