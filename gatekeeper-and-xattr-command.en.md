# About Gatekeeper and xattr command

When we enable Gatekeeper, the user can install apps through App Store or identified developers.

The macOS has `xattr` command.

```sh
xattr -c xxx.app
# or
xattr -r -d com.apple.quarantine xxx.app
```

As described above, the user can remove `com.apple.quarantine` custom attributes from the app.


The problem here is that if you use the `xattr` command to remove custom attributes for applications that are unsigned
Even with Gatekepper enabled, you can escape Gatekeeper censorship.
Threfore, if an organization has prepared a policy to force Gatekepper in the configuration profile, it does not make sense.


What opinion does Apple have about these events?
Also, do we have a workaround for this problem?

The individual questioner thinks that the point at which companies allow the escape of the `xattr` command is vulnerable.

## Apple answer

This is by design. It is not vulnerable to security because it was deleted by the user.

Even if GateKeeper enable / disable settings are restricted to the administrator only, if you have any problem with the ability to delete extended attributes with user authority, please report it as feedback in [Feedback Assistant](https://feedbackassistant.apple.com/).
