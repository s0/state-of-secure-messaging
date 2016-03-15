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
| Contact Discovery       | Mobile Number     | ?              | ![](cross.png) | ?      | ?              |
| Offline Messaging       | ![](tick.png)     | ![](cross.png) | ![](cross.png) | ?      | ![](tick.png)  |
| Group Messaging         | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Multi-Device Support    | ![](tick.png) (3) | In Development | ![](cross.png) | ?      | ![](cross.png) |
| Calling                 | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Video Chat              | ![](cross.png)    | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) |
| Deniability             | ![](tick.png)     | ![](tick.png)  | ?              | ?      | ?              |
| Forward Secrecy         | ![](tick.png)     | ![](tick.png)  | ?              | ?      | ?              |
| Future Secrecy          | ![](tick.png)     | ?              | ?              | ?      | ?              |

## Metadata Leakage

Information (that is not part of the content of a message) that may be
undesirable for others to know about.

Again this is just a very quick list of things I could think of that could be
considered metadata. Suggestions welcome.

**Key:**
 * `-` leak does not matter / makes no sense.
 * ![](cross.png) the data is leaked.
 * ![](tick.png) the data is not leaked.
 * `?` needs clarification / investigation.

| Data                            | Observer |      Tox       |    Ricochet    |  Pond  |  Twister DMs   |
| :------------------------------ | :------- | :------------: | :------------: | :----: | :------------: |
| Usage                           | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ![](cross.png) |
| Usage                           | Public   | ![](tick.png)  | ![](tick.png)  | ?      | ![](cross.png) |
| Usage                           | Contact  | -              | -              | -      | -              |
| Contacts                        | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ?              |
| Contacts                        | Public   | ?              | ![](tick.png)  | ?      | ![](cross.png) |
| Contacts                        | Contact  | ?              | ![](tick.png)  | ?      | ![](cross.png) |
| IP Address                      | Edge     | -              | -              | -      | -              |
| IP Address                      | Public   | ![](tick.png)  | ![](tick.png)  | ?      | ?              |
| IP Address                      | Contact  | ![](cross.png) | ![](tick.png)  | ?      | ?              |
| Currently Communicating Parties | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ?              |
| Recipients of Outgoing Traffic  | Edge     | ![](cross.png) | ![](tick.png)  | ?      | ![](tick.png)  |

**Data Definitions:**

* **Usage:** The observer can see when you are using the given system, or even
  just the fact that you *do* use it, or have used it in the past.
* **Contacts:** The observer can see one or more associations (either IP
  Address or Identifier on System) between you and someone else.

  If for example an edge observer could observe a connection between you and
  another user of the same system (e.g. a direct TCP connection between 2 IP
  Addresses) then this counts as a leak of this kind. Over time an adversary
  could build up a map of all of your "contacts" presuming you message each of
  your contacts at least once since observation begins.
* **IP Address:** Self Explanatory. Can be tied to a geographic location and
  your identity in many situations.


**Observer Definitions:**

* **Edge:** Nearby network infrastructure, so your local network, ISP, NSA and any
  network you may connect to as a guest or otherwise all count as entities that
  can observe edge traffic, in essence anyone between you and the "system".

  **Has Information:**
  * IP Address
  * Physical Location
  * Real Identity

* **Public:** Any person on the internet / whether using the system or not.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)

* **Contact:** Someone on your contact's list.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)


