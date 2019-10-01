# Ncom

[![Actions Status](https://github.com/harry-harris-27/Ncom/workflows/Ncom%20CI/badge.svg)](https://github.com/harry-harris-27/Ncom/actions)

A small portable .NET library built for the encoding and decoding the [OxTS](https://www.oxts.com/) NCOM binary data packet. 

Note that this library is not complete:
- [ ] Finish adding Status Channel Enumerations.
- [ ] Finish implementing Status Channels.
- [ ] Test thoroughly. :)

## Code Example
### Decoding
```C#
// Get Ncom data from somewhere. E.g. an UDP packet.
byte[] data;

List<NcomPacket> pkts = new NcomPacketFactory().ProcessNcom(data, 0);
foreach (NcomPacket pkt in pkts)
{
    NcomPacketA ncomData = pkt as NcomPacketA;  // Check that decoded packet was of type Structure-A.
    if (ncomData != null)
    {
        // Here we have our decoded NCOM data.
        // ...
    }
}
```
or
```C#
// Decoding a single NCOM packet
NcomPacketA pkt = new NcomPacketA();

// Get NCOM data from somewhere
byte[] data;

// Decode
pkt.Unmarshal(data, 0);
```

### Encoding
```C#
NcomPacketA ncom = new NcomPacketA();

// ...

byte[] encoded = ncom.Marshal();

// Now do want you want with marshalled NCOM data. E.g. send out in UDP packet.
// ...
```
