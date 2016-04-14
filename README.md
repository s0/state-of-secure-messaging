# State of Secure Messaging

This document is intended to be a high-level summary of the various features /
characteristics of current open source secure messaging systems. This document
only covers **completely open source end-to-end encrypted systems** (by systems,
I mean the underlying network architecture and protocol, not specific client
implementations).

In essence, for all of these systems, all content of messages is encrypted on
the sender and receiver's devices.

### Note

This document is a very rough draft, and there is still lots of work left to be
done.

## Features

| Feature                 |      Signal       |      Tox       |    Ricochet    |  Pond  |  Twister DMs   | RetroShare     |
| :---------------------- | :---------------: | :------------: | :------------: | :----: | :------------: | :------------: |
| Architecture            | Central           | P2P            | P2P            | ?      | P2P            | F2F            |
| Hidden Metadata         | ![](cross.png)    | Some           | ![](tick.png)  | ?      | Some           | Some           |
| Censorship Resistant    | ![](cross.png)    | ?              | ![](tick.png)  | ?      | ![](tick.png)  | ![](tick.png)  |
| Contact Discovery       | Mobile Number     | ?              | ![](cross.png) | ?      | ?              | ?              |
| Offline Messaging       | ![](tick.png)     | ![](cross.png) | ![](cross.png) | ?      | ![](tick.png)  | ![](tick.png)  |
| Group Messaging         | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) | ![](tick.png)  |
| Multi-Device Support    | ![](tick.png) (3) | In Development | ![](cross.png) | ?      | ![](cross.png) | ![](cross.png) |
| Calling                 | ![](tick.png)     | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) | ![](tick.png)  |
| Video Chat              | ![](cross.png)    | ![](tick.png)  | ![](cross.png) | ?      | ![](cross.png) | ![](tick.png)  |
| Deniability             | ![](tick.png)     | ![](tick.png)  | ?              | ?      | ?              | ?              |
| Forward Secrecy         | ![](tick.png)     | ![](tick.png)  | ?              | ?      | ?              | ![](tick.png)  |
| Future Secrecy          | ![](tick.png)     | ?              | ?              | ?      | ?              | ?              |

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

| Data                                  | Observer |     Signal     |      Tox       |  Tox over Tor  |    Ricochet    |  Pond  |  Twister DMs   | RS over Tor |
| :------------------------------------ | :------- | :------------: |:-------------: | :------------: | :------------: | :----: | :------------: | :-----------: |
| Usage                                 | Edge     | ![](cross.png) | ![](cross.png) | ![](tick.png)  | ![](tick.png)  | ?      | ![](cross.png) | ![](tick.png) |
| Usage                                 | Server   | ![](cross.png) | -              | -              | -              | ?      | -              | -             |
| Usage                                 | Public   | ![](cross.png) | ![](tick.png)  | ![](tick.png)  | ![](tick.png)  | ?      | ![](cross.png) | ![](tick.png) |
| Usage                                 | Contact  | -              | -              | -              | -              | -      | -              | -             |
| Contacts Currently Communicating With | Edge     | ![](tick.png)  | ![](cross.png) | ![](tick.png)  | ![](tick.png)  | ?      | ![](tick.png)  | ![](tick.png) |
| Contacts Currently Communicating With | Server   | ![](cross.png) | -              | -              | -              | ?      | -              | -             | 
| Contacts Currently Communicating With | Public   | ![](tick.png)  | ?              | ?              | ![](tick.png)  | ?      | ![](tick.png)  | ![](tick.png) |
| Contacts Currently Communicating With | Contact  | ![](tick.png)  | ?              | ?              | ![](tick.png)  | ?      | ![](tick.png)  | ![](tick.png) |
| Contacts                              | Edge     | ![](tick.png)  | ![](cross.png) | ![](tick.png)  | ![](tick.png)  | ?      | ?              | ![](tick.png) |
| Contacts                              | Server   | ![](cross.png) | -              | -              | -              | ?      | -              | -             |
| Contacts                              | Public   | ![](tick.png)  | ?              | ?              | ![](tick.png)  | ?      | ![](cross.png) | ![](tick.png) |
| Contacts                              | Contact  | ![](tick.png)  | ?              | ?              | ![](tick.png)  | ?      | ![](cross.png) | ![](tick.png) |
| IP Address                            | Edge     | -              | -              | -              | -              | -      | -              | -             |
| IP Address                            | Server   | ![](cross.png) | -              | -              | -              | ?      | -              | -             |
| IP Address                            | Public   | ![](tick.png)  | ![](tick.png)  | ![](tick.png)  | ![](tick.png)  | ?      | ?              | ![](tick.png) |
| IP Address                            | Contact  | ![](tick.png)  | ![](cross.png) | ![](tick.png)  | ![](tick.png)  | ?      | ?              | ![](tick.png) |

**Data Definitions:**

* **Usage:** The observer can see when you are using the given system, or even
  just the fact that you *do* use it, or have used it in the past.
* **Contacts Currently Communicating With:** The oberver can see when you are
  communicating with a particular contact (either IP Address or Identifier on
  System). A leak of this kind directly leads to a leak of **Contacts** as
  detailed below. Seeing a single message while knowing the sender and recipient
  counts as a leak of this kind.

  From the point of view of the Contact observer, we exclude communications only
  with this contact. IE: we consider there to be a leak only when one contact
  can see you communicating with a different contact.
* **Contacts:** The observer can see one or more associations (either IP
  Address or Identifier on System) between you and someone else.

  If for example an edge observer could observe a connection between you and
  another user of the same system (as above) (e.g. a direct TCP connection
  between 2 IP Addresses) then this counts as a leak of this kind. Over time an
  adversary could build up a map of all of your "contacts" presuming you message
  each of your contacts at least once since observation begins.
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

* **Server:** Only applicable to Centralized systems.

  **Has Information:**
  * IP Address (and potentially other associated information)
  * Identifier on system

* **Public:** Any person on the internet / whether using the system or not.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)

* **Contact:** Someone on your contact's list.

  **Has Information:**
  * Identifier on system (e.g. username / pubkey)
