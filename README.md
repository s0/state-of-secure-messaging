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
| Hidden Metadata         | ![](cross.png)    | Some           | ![](tick.png)  | ?      | Some           |
| Censorship Resistant    | ![](cross.png)    | ?              | ![](tick.png)  | ?      | ![](tick.png)  |
| Contact Discovery       | ![](tick.png)     | ?              | ![](cross.png) | ?      | ?              |
| Offline Messaging       | ![](tick.png)     | ![](cross.png) | ![](cross.png) | ?      | ![](tick.png)  |
| Group Messaging         | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Multi-Device Support    | ![](tick.png) (3) | ![](cross.png) | ![](cross.png) | ?      | ![](cross.png) |
| Calling                 | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Video Chat              | ![](cross.png)    | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Deniability             | ![](tick.png)     | ?              | ?              | ?      | ?              |
| Forward Secrecy         | ![](tick.png)     | ![](tick.png)  | ?              | ?      | ?              |
| Future Secrecy          | ![](tick.png)     | ?              | ?              | ?      | ?              |

## Metadata Leaking

When it comes to metadata, there are many different pieces of data that can be
considered metadata. This table attempts to summarize how well each of these
systems does at hiding metadata.

Again this is just a very quick list of things I could think of that make up
metadata.

| Data                            | Observer |      Tox       |    Ricochet    |  Pond  |  Twister DMs   |
| :------------------------------ | :------- | :------------: | :------------: | :----: | :------------: |
| Usage                           | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ![](cross.png) |
| Usage                           | Public   | ![](tick.png)  | ![](tick.png)  | ?      | ![](cross.png) |
| Contact List                    | Public   | ?              | ![](tick.png)  | ?      | ![](cross.png) |
| Contact List                    | Edge     | ?              | ![](tick.png)  | ?      | ![](cross.png) |
| Contact List                    | Contact  | ?              | ![](tick.png)  | ?      | ![](cross.png) |
| Currently Communicating Parties | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ?              |
| Recipients of Outgoing Traffic  | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ![](tick.png)  |
| IP Address                      | Public   | ![](tick.png)  | ![](tick.png)  | ?      | ?              |
| IP Address                      | Contact  | ![](cross.png) | ![](tick.png)  | ?      | ?              |

**Definitions**:

* Edge: Nearby network infrastructure, so your local network, ISP, NSA all count
  as entities that can observe edge traffic, in essence anyone between you and
  the "system".

  **Has Information:**
  * IP Address
  * Physical Location
  * Potentially Real Identity
* Public: Any person on the internet / whether using the system or not.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)

* Contact: Someone on your contact's list.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)


