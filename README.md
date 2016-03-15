# State of Secure Messaging

This document is intended to be a high-level summary of the various features /
characteristics of current open source secure messaging systems. This document
only covers completely open source end-to-end encrypted systems.

In essence, for all of these systems, all content of messages is encrypted on
the sender and receiver's devices.

## Under Development

This is a very rough draft of this information and there is still lots of work
left to be done.

| Feature                 |      Signal       |      Tox       |    Ricochet    |  Pond  |  Twister DMs   |
| :---------------------- | :---------------: | :------------: | :------------: | :----: | :------------: |
| Architecture            | Central           | P2P            | P2P            | ?      | P2P            |
| Hidden Metadata         | ![](cross.png)    | ?              | ![](tick.png)  | ?      | Some           |
| Censorship Resistance   | ![](cross.png)    | ?              | ![](tick.png)  | ?      | ![](tick.png)  |
| Contact Discovery       | ![](tick.png)     | ?              | ![](cross.png) | ?      | ?              |
| Offline Messaging       | ![](tick.png)     | ![](cross.png) | ![](cross.png) | ?      | ![](tick.png)  |
| Group Messaging         | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Multi-Device Support    | ![](tick.png) (3) | ![](cross.png) | ![](cross.png) | ?      | ![](cross.png) |
| Calling                 | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Video Chat              | ![](cross.png)    | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Deniability             | ![](tick.png)     | ?              | ?              | ?      | ?              |
| Forward Secrecy         | ![](tick.png)     | ?              | ?              | ?      | ?              |
| Future Secrecy          | ![](tick.png)     | ?              | ?              | ?      | ?              |
