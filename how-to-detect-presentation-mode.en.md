# How to detect presentation mode

In an organization, the IT adminstrator may want to force software updates.
Depending on the contents of software update and application update, there are cases where it is necessary to restart the OS.

We often have a requirement to refrain from restarting, as it may affect the business during presentation in presentation mode (or during online MTG using a camera or microphone).
To do this, we need to use some means, preferably using the command line, to determine if the device is currently presenting (or on-line MTG using a camera or microphone).

How can we determine "presentation mode (or using a camera or microphone)"?

## Apple answer

There is currently no easy way to do this.
Please submit a Feature Request if necessary.

## Workaround I think

We can identify it for each application.

```sh
# For example, detecting presentation mode of "Microsoft PowerPoint" app
/usr/bin/lsappinfo info -only presentationmode "Microsoft PowerPoint" | /usr/bin/grep "AllHidden"
```

The `UIPresentationMode` status can be obtained by `lsappinfo info -only presentationmode`, so the presentation mode can be detected from this output result.
