[[Ubuntu-core]] model-file creation [guide](https://ubuntu.com/core/docs/create-model-assertion).

At the heart of custom Ubuntu Core image creation is the _model assertion_. An assertion is a signed recipe that describes the components that comprise a complete image. An assertion is provided as JSON in a text file which is signed by a GPG key associated with the publisher’s Ubuntu One account.

The model contains:

- identification information, such as the developer-id and model name.
- which [essential snaps](https://ubuntu.com/core/docs/components#heading--system) make up the device system.
- other required or optional snaps that implement the device functionality.

After a model has been [created or modified](https://ubuntu.com/core/docs/create-model-assertion), it must be signed with a GPG key to become a _model assertion_. This ensures the model cannot be altered without the key and also links the created image to both the signed version of the model and your Ubuntu One account.

This is accomplished in three stages:
- [1. Create a key](https://ubuntu.com/core/docs/sign-model-assertion#heading--signing-1)
- [2. Register the key](https://ubuntu.com/core/docs/sign-model-assertion#heading--signing-2)
- [3. Sign the model](https://ubuntu.com/core/docs/sign-model-assertion#heading--signing-3)
