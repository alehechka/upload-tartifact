# upload-tartifact

Composite GitHub Action that solves for a shortcoming of the current [upload-artifact](https://github.com/actions/upload-artifact) action, in which any artifacts downloaded lose their file privileges (namely, execution privilege).

This action will first tar any files or folders at the provided `path` input into an `artifact.tar` at the root of the GHA environment. Then `actions/upload-artifact@v2` is used directly to artifact the tar file. Once completed, this action will clean itself up by removing the `artifact.tar` file.

Utilize the sibling action at [download-tartifact](https://github.com/alehechka/download-tartifact) to download the artifact and extract your files.

> Note: The `path` provided will be maintained through tar, so after download-tartifact, and subfolder structure will remain intact.
