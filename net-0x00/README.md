* Periksa terlebih dulu jenis berkas _net-0x00.pcap_ (langkah ini sifatnya opsional):

```
% file net-0x00.pcap
net-0x00.pcap: tcpdump capture file (little-endian) - version 2.4 (Ethernet, capture length 65535)
```

* Setelah mengetahui format berkas tersebut. Lanjutkan dengan membukanya menggunakan aplikasi tcpdump/wireshark/tshark atau semacamnya. Pada tutorial ini, akan digunakan tshark. Jalankan aplikasi tshark untuk membaca berkas _net-0x00.pcap_ menggunakan perintah seperti ini:

```
% tshark -2Vxr net-0x00.pcap
```

* Penjelasan untuk opsi yang diberikan di atas adalah sebagai berikut:
  * __-2__ adalah opsi untuk melakukan analisa paket sebanyak 2 kali.
  * __-V__ adalah opsi untuk menampilkan paket dalam bentuk struktur pohon.
  * __-x__ adalah opsi untuk menampilkan paket dalam format heksadesimal dan ASCII
  * __-r__ adalah opsi untuk membaca paket dari berkas yang diinginkan.

* Berikut ini adalah hasil yang diperoleh setelah menjalankan instruksi di atas:

```
Frame 1: 125 bytes on wire (1000 bits), 125 bytes captured (1000 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Mar 30, 2012 22:40:11.863928000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1333122011.863928000 seconds
    [Time delta from previous captured frame: 0.000000000 seconds]
    [Time delta from previous displayed frame: 0.000000000 seconds]
    [Time since reference or first frame: 0.000000000 seconds]
    Frame Number: 1
    Frame Length: 125 bytes (1000 bits)
    Capture Length: 125 bytes (1000 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:udp:radius]
Ethernet II, Src: 00:50:56:b8:39:67 (00:50:56:b8:39:67), Dst: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
    Destination: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        Address: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        Address: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 111
    Identification: 0x5681 (22145)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 128
    Protocol: UDP (17)
    Header checksum: 0xcfc6 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
User Datagram Protocol, Src Port: 59916 (59916), Dst Port: radius (1812)
    Source Port: 59916 (59916)
    Destination Port: radius (1812)
    Length: 91
    Checksum: 0x0baa [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
    [Stream index: 0]
Radius Protocol
    Code: Access-Request (1)
    Packet identifier: 0xb0 (176)
    Length: 83
    Authenticator: d82373c55f983a63348d47070a0c36f0
    [The response to this request is in frame 2]
    Attribute Value Pairs
        AVP: l=6 t=NAS-IP-Address(4): 10.10.20.214
            NAS-IP-Address: 10.10.20.214 (10.10.20.214)
        AVP: l=6 t=NAS-Port(5): 1
            NAS-Port: 1
        AVP: l=15 t=User-Name(1): Administrator
            User-Name: Administrator
        AVP: l=18 t=User-Password(2): Encrypted
            User-Password (encrypted): a60427af57776a2bc69a95d6995655c3
        AVP: l=18 t=Message-Authenticator(80): 3e26dc66bb610f05597850c19412f4f0
            Message-Authenticator: 3e26dc66bb610f05597850c19412f4f0

0000  00 50 56 b8 39 61 00 50 56 b8 39 67 08 00 45 00   .PV.9a.PV.9g..E.
0010  00 6f 56 81 00 00 80 11 cf c6 0a 00 00 0d 0a 00   .oV.............
0020  00 2a ea 0c 07 14 00 5b 0b aa 01 b0 00 53 d8 23   .*.....[.....S.#
0030  73 c5 5f 98 3a 63 34 8d 47 07 0a 0c 36 f0 04 06   s._.:c4.G...6...
0040  0a 0a 14 d6 05 06 00 00 00 01 01 0f 41 64 6d 69   ............Admi
0050  6e 69 73 74 72 61 74 6f 72 02 12 a6 04 27 af 57   nistrator....'.W
0060  77 6a 2b c6 9a 95 d6 99 56 55 c3 50 12 3e 26 dc   wj+.....VU.P.>&.
0070  66 bb 61 0f 05 59 78 50 c1 94 12 f4 f0            f.a..YxP.....

Frame 2: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Mar 30, 2012 22:40:13.293006000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1333122013.293006000 seconds
    [Time delta from previous captured frame: 1.429078000 seconds]
    [Time delta from previous displayed frame: 1.429078000 seconds]
    [Time since reference or first frame: 1.429078000 seconds]
    Frame Number: 2
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:udp:radius]
Ethernet II, Src: 00:50:56:b8:39:61 (00:50:56:b8:39:61), Dst: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
    Destination: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        Address: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        Address: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.42 (10.0.0.42), Dst: 10.0.0.13 (10.0.0.13)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x619a (24986)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 128
    Protocol: UDP (17)
    Header checksum: 0xc4c0 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.42 (10.0.0.42)
    Destination: 10.0.0.13 (10.0.0.13)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
User Datagram Protocol, Src Port: radius (1812), Dst Port: 59916 (59916)
    Source Port: radius (1812)
    Destination Port: 59916 (59916)
    Length: 72
    Checksum: 0x1fbc [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
    [Stream index: 0]
Radius Protocol
    Code: Access-Challenge (11)
    Packet identifier: 0xb0 (176)
    Length: 64
    Authenticator: 7555b022d9d547168a4ddfd86938ebec
    [This is a response to a request in frame 1]
    [Time from request: 1.429078000 seconds]
    Attribute Value Pairs
        AVP: l=36 t=Reply-Message(18): Please enter your onetime password
            Reply-Message: Please enter your onetime password
        AVP: l=8 t=State(24): 773031616545
            State: 773031616545

0000  00 50 56 b8 39 67 00 50 56 b8 39 61 08 00 45 00   .PV.9g.PV.9a..E.
0010  00 5c 61 9a 00 00 80 11 c4 c0 0a 00 00 2a 0a 00   .\a..........*..
0020  00 0d 07 14 ea 0c 00 48 1f bc 0b b0 00 40 75 55   .......H.....@uU
0030  b0 22 d9 d5 47 16 8a 4d df d8 69 38 eb ec 12 24   ."..G..M..i8...$
0040  50 6c 65 61 73 65 20 65 6e 74 65 72 20 79 6f 75   Please enter you
0050  72 20 6f 6e 65 74 69 6d 65 20 70 61 73 73 77 6f   r onetime passwo
0060  72 64 18 08 77 30 31 61 65 45                     rd..w01aeE

Frame 3: 133 bytes on wire (1064 bits), 133 bytes captured (1064 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Mar 30, 2012 22:40:21.342231000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1333122021.342231000 seconds
    [Time delta from previous captured frame: 8.049225000 seconds]
    [Time delta from previous displayed frame: 8.049225000 seconds]
    [Time since reference or first frame: 9.478303000 seconds]
    Frame Number: 3
    Frame Length: 133 bytes (1064 bits)
    Capture Length: 133 bytes (1064 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:udp:radius]
Ethernet II, Src: 00:50:56:b8:39:67 (00:50:56:b8:39:67), Dst: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
    Destination: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        Address: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        Address: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 119
    Identification: 0x56b9 (22201)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 128
    Protocol: UDP (17)
    Header checksum: 0xcf86 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
User Datagram Protocol, Src Port: 59917 (59917), Dst Port: radius (1812)
    Source Port: 59917 (59917)
    Destination Port: radius (1812)
    Length: 99
    Checksum: 0xe426 [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
    [Stream index: 1]
Radius Protocol
    Code: Access-Request (1)
    Packet identifier: 0x13 (19)
    Length: 91
    Authenticator: 70dadac292ee94f668ac33e0ae2c416d
    [The response to this request is in frame 4]
    Attribute Value Pairs
        AVP: l=6 t=NAS-IP-Address(4): 10.10.20.214
            NAS-IP-Address: 10.10.20.214 (10.10.20.214)
        AVP: l=6 t=NAS-Port(5): 1
            NAS-Port: 1
        AVP: l=8 t=State(24): 773031616545
            State: 773031616545
        AVP: l=15 t=User-Name(1): Administrator
            User-Name: Administrator
        AVP: l=18 t=User-Password(2): Encrypted
            User-Password (encrypted): 0396218359d7845fa2ba82bb05285570
        AVP: l=18 t=Message-Authenticator(80): 89188ce92a2c5b81a46fe1633f9a033c
            Message-Authenticator: 89188ce92a2c5b81a46fe1633f9a033c

0000  00 50 56 b8 39 61 00 50 56 b8 39 67 08 00 45 00   .PV.9a.PV.9g..E.
0010  00 77 56 b9 00 00 80 11 cf 86 0a 00 00 0d 0a 00   .wV.............
0020  00 2a ea 0d 07 14 00 63 e4 26 01 13 00 5b 70 da   .*.....c.&...[p.
0030  da c2 92 ee 94 f6 68 ac 33 e0 ae 2c 41 6d 04 06   ......h.3..,Am..
0040  0a 0a 14 d6 05 06 00 00 00 01 18 08 77 30 31 61   ............w01a
0050  65 45 01 0f 41 64 6d 69 6e 69 73 74 72 61 74 6f   eE..Administrato
0060  72 02 12 03 96 21 83 59 d7 84 5f a2 ba 82 bb 05   r....!.Y.._.....
0070  28 55 70 50 12 89 18 8c e9 2a 2c 5b 81 a4 6f e1   (UpP.....*,[..o.
0080  63 3f 9a 03 3c                                    c?..<

Frame 4: 62 bytes on wire (496 bits), 62 bytes captured (496 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Mar 30, 2012 22:40:21.345618000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1333122021.345618000 seconds
    [Time delta from previous captured frame: 0.003387000 seconds]
    [Time delta from previous displayed frame: 0.003387000 seconds]
    [Time since reference or first frame: 9.481690000 seconds]
    Frame Number: 4
    Frame Length: 62 bytes (496 bits)
    Capture Length: 62 bytes (496 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:udp:radius]
Ethernet II, Src: 00:50:56:b8:39:61 (00:50:56:b8:39:61), Dst: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
    Destination: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        Address: 00:50:56:b8:39:67 (00:50:56:b8:39:67)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        Address: 00:50:56:b8:39:61 (00:50:56:b8:39:61)
        .... ..0. .... .... .... .... = LG bit: Globally unique address (factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.42 (10.0.0.42), Dst: 10.0.0.13 (10.0.0.13)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 48
    Identification: 0x62a0 (25248)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 128
    Protocol: UDP (17)
    Header checksum: 0xc3e6 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.42 (10.0.0.42)
    Destination: 10.0.0.13 (10.0.0.13)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
User Datagram Protocol, Src Port: radius (1812), Dst Port: 59917 (59917)
    Source Port: radius (1812)
    Destination Port: 59917 (59917)
    Length: 28
    Checksum: 0x689b [validation disabled]
        [Good Checksum: False]
        [Bad Checksum: False]
    [Stream index: 1]
Radius Protocol
    Code: Access-Accept (2)
    Packet identifier: 0x13 (19)
    Length: 20
    Authenticator: 8a53eb0bcdb3caa5f9638a9b2b83d25f
    [This is a response to a request in frame 3]
    [Time from request: 0.003387000 seconds]

0000  00 50 56 b8 39 67 00 50 56 b8 39 61 08 00 45 00   .PV.9g.PV.9a..E.
0010  00 30 62 a0 00 00 80 11 c3 e6 0a 00 00 2a 0a 00   .0b..........*..
0020  00 0d 07 14 ea 0d 00 1c 68 9b 02 13 00 14 8a 53   ........h......S
0030  eb 0b cd b3 ca a5 f9 63 8a 9b 2b 83 d2 5f         .......c..+.._

Frame 5: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000000000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000000000 seconds
    [Time delta from previous captured frame: 113832194.654382000 seconds]
    [Time delta from previous displayed frame: 113832194.654382000 seconds]
    [Time since reference or first frame: 113832204.136072000 seconds]
    Frame Number: 5
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x666a [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0xcb39 [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 5]
            [No response seen to ICMP request in frame 5]
            [Severity level: Warn]
            [Group: Sequence]
    Data (64 bytes)
        Data: 376133376166626331633237303330306535343431623439...
        [Length: 64]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 5c 00 01 00 00 40 01 66 6a 0a 00 00 0d 0a 00   .\....@.fj......
0020  00 2a 08 00 cb 39 00 00 00 00 37 61 33 37 61 66   .*...9....7a37af
0030  62 63 31 63 32 37 30 33 30 30 65 35 34 34 31 62   bc1c270300e5441b
0040  34 39 30 30 32 30 30 30 30 30 30 30 30 30 30 30   4900200000000000
0050  30 30 30 30 36 33 30 30 30 30 30 30 30 30 30 30   0000630000000000
0060  30 30 33 61 62 64 62 64 38 31                     003abdbd81

Frame 6: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000001000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000001000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832204.136073000 seconds]
    Frame Number: 6
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x666a [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x4d01 [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 6]
            [No response seen to ICMP request in frame 6]
            [Severity level: Warn]
            [Group: Sequence]
    Data (64 bytes)
        Data: 616532336430343731326434666235623261646335373664...
        [Length: 64]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 5c 00 01 00 00 40 01 66 6a 0a 00 00 0d 0a 00   .\....@.fj......
0020  00 2a 08 00 4d 01 00 00 00 00 61 65 32 33 64 30   .*..M.....ae23d0
0030  34 37 31 32 64 34 66 62 35 62 32 61 64 63 35 37   4712d4fb5b2adc57
0040  36 64 36 39 37 31 38 35 63 61 63 35 31 37 37 62   6d697185cac5177b
0050  63 64 63 39 37 34 36 39 35 63 35 66 32 37 32 30   cdc974695c5f2720
0060  39 32 65 65 65 32 37 37 38 66                     92eee2778f

Frame 7: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000002000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000002000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832204.136074000 seconds]
    Frame Number: 7
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x666a [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x0b00 [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 7]
            [No response seen to ICMP request in frame 7]
            [Severity level: Warn]
            [Group: Sequence]
    Data (64 bytes)
        Data: 303430313030303630393031303032303062303730303031...
        [Length: 64]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 5c 00 01 00 00 40 01 66 6a 0a 00 00 0d 0a 00   .\....@.fj......
0020  00 2a 08 00 0b 00 00 00 00 00 30 34 30 31 30 30   .*........040100
0030  30 36 30 39 30 31 30 30 32 30 30 62 30 37 30 30   06090100200b0700
0040  30 31 32 34 30 32 66 31 30 36 30 31 30 37 35 33   012402f106010753
0050  30 61 62 33 30 37 33 35 64 34 32 38 66 36 30 33   0ab30735d428f603
0060  34 63 32 33 30 33 30 31 30 33                     4c23030103

Frame 8: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000003000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000003000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832204.136075000 seconds]
    Frame Number: 8
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x666a [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x658f [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 8]
            [No response seen to ICMP request in frame 8]
            [Severity level: Warn]
            [Group: Sequence]
    Data (64 bytes)
        Data: 303530313030356430313030303130303063303031383163...
        [Length: 64]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 5c 00 01 00 00 40 01 66 6a 0a 00 00 0d 0a 00   .\....@.fj......
0020  00 2a 08 00 65 8f 00 00 00 00 30 35 30 31 30 30   .*..e.....050100
0030  35 64 30 31 30 30 30 31 30 30 30 63 30 30 31 38   5d010001000c0018
0040  31 63 30 38 30 30 30 31 30 61 63 62 34 36 63 39   1c0800010acb46c9
0050  36 31 30 30 30 30 30 31 30 35 31 33 31 31 36 36   6100000105131166
0060  30 30 36 63 30 30 36 31 30 30                     006c006100

Frame 9: 106 bytes on wire (848 bits), 106 bytes captured (848 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000004000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000004000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832204.136076000 seconds]
    Frame Number: 9
    Frame Length: 106 bytes (848 bits)
    Capture Length: 106 bytes (848 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 92
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x666a [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x1942 [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 9]
            [No response seen to ICMP request in frame 9]
            [Severity level: Warn]
            [Group: Sequence]
    Data (64 bytes)
        Data: 363730303265303037343030373830303734303030303030...
        [Length: 64]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 5c 00 01 00 00 40 01 66 6a 0a 00 00 0d 0a 00   .\....@.fj......
0020  00 2a 08 00 19 42 00 00 00 00 36 37 30 30 32 65   .*...B....67002e
0030  30 30 37 34 30 30 37 38 30 30 37 34 30 30 30 30   0074007800740000
0040  30 30 31 34 30 30 30 31 30 61 38 30 30 30 34 39   001400010a800049
0050  34 37 36 31 63 39 64 31 31 39 31 35 30 31 30 31   4761c9d119150101
0060  30 36 32 30 30 30 61 34 38 30                     062000a480

Frame 10: 60 bytes on wire (480 bits), 60 bytes captured (480 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:43:36.000005000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954216.000005000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832204.136077000 seconds]
    Frame Number: 10
    Frame Length: 60 bytes (480 bits)
    Capture Length: 60 bytes (480 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
    Padding: 00000000000000000000
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 36
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x66a2 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x2f3e [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 10]
            [No response seen to ICMP request in frame 10]
            [Severity level: Warn]
            [Group: Sequence]
    Data (8 bytes)
        Data: 3030383130303030
        [Length: 8]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 24 00 01 00 00 40 01 66 a2 0a 00 00 0d 0a 00   .$....@.f.......
0020  00 2a 08 00 2f 3e 00 00 00 00 30 30 38 31 30 30   .*../>....008100
0030  30 30 00 00 00 00 00 00 00 00 00 00               00..........

Frame 11: 64 bytes on wire (512 bits), 64 bytes captured (512 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:44:08.000000000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954248.000000000 seconds
    [Time delta from previous captured frame: 31.999995000 seconds]
    [Time delta from previous displayed frame: 31.999995000 seconds]
    [Time since reference or first frame: 113832236.136072000 seconds]
    Frame Number: 11
    Frame Length: 64 bytes (512 bits)
    Capture Length: 64 bytes (512 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 50
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x6694 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x3efa [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 11]
            [No response seen to ICMP request in frame 11]
            [Severity level: Warn]
            [Group: Sequence]
    Data (22 bytes)
        Data: 77007500b7005100fa004400a1003300d100e2000000
        [Length: 22]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 32 00 01 00 00 40 01 66 94 0a 00 00 0d 0a 00   .2....@.f.......
0020  00 2a 08 00 3e fa 00 00 00 00 77 00 75 00 b7 00   .*..>.....w.u...
0030  51 00 fa 00 44 00 a1 00 33 00 d1 00 e2 00 00 00   Q...D...3.......

Frame 12: 64 bytes on wire (512 bits), 64 bytes captured (512 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:44:08.000001000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954248.000001000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832236.136073000 seconds]
    Frame Number: 12
    Frame Length: 64 bytes (512 bits)
    Capture Length: 64 bytes (512 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 50
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x6694 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x14fc [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 12]
            [No response seen to ICMP request in frame 12]
            [Severity level: Warn]
            [Group: Sequence]
    Data (22 bytes)
        Data: 3c0036003600a8009d0055000100ab0024007b005600
        [Length: 22]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 32 00 01 00 00 40 01 66 94 0a 00 00 0d 0a 00   .2....@.f.......
0020  00 2a 08 00 14 fc 00 00 00 00 3c 00 36 00 36 00   .*........<.6.6.
0030  a8 00 9d 00 55 00 01 00 ab 00 24 00 7b 00 56 00   ....U.....$.{.V.

Frame 13: 64 bytes on wire (512 bits), 64 bytes captured (512 bits)
    Encapsulation type: Ethernet (1)
    Arrival Time: Nov  8, 2015 10:44:08.000002000 WIB
    [Time shift for this packet: 0.000000000 seconds]
    Epoch Time: 1446954248.000002000 seconds
    [Time delta from previous captured frame: 0.000001000 seconds]
    [Time delta from previous displayed frame: 0.000001000 seconds]
    [Time since reference or first frame: 113832236.136074000 seconds]
    Frame Number: 13
    Frame Length: 64 bytes (512 bits)
    Capture Length: 64 bytes (512 bits)
    [Frame is marked: False]
    [Frame is ignored: False]
    [Protocols in frame: eth:ethertype:ip:icmp:data]
Ethernet II, Src: 0a:01:01:01:01:01 (0a:01:01:01:01:01), Dst: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
    Destination: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        Address: 0a:02:02:02:02:02 (0a:02:02:02:02:02)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Source: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        Address: 0a:01:01:01:01:01 (0a:01:01:01:01:01)
        .... ..1. .... .... .... .... = LG bit: Locally administered address (this is NOT the factory default)
        .... ...0 .... .... .... .... = IG bit: Individual address (unicast)
    Type: IP (0x0800)
Internet Protocol Version 4, Src: 10.0.0.13 (10.0.0.13), Dst: 10.0.0.42 (10.0.0.42)
    Version: 4
    Header Length: 20 bytes
    Differentiated Services Field: 0x00 (DSCP 0x00: Default; ECN: 0x00: Not-ECT (Not ECN-Capable Transport))
        0000 00.. = Differentiated Services Codepoint: Default (0x00)
        .... ..00 = Explicit Congestion Notification: Not-ECT (Not ECN-Capable Transport) (0x00)
    Total Length: 50
    Identification: 0x0001 (1)
    Flags: 0x00
        0... .... = Reserved bit: Not set
        .0.. .... = Don't fragment: Not set
        ..0. .... = More fragments: Not set
    Fragment offset: 0
    Time to live: 64
    Protocol: ICMP (1)
    Header checksum: 0x6694 [validation disabled]
        [Good: False]
        [Bad: False]
    Source: 10.0.0.13 (10.0.0.13)
    Destination: 10.0.0.42 (10.0.0.42)
    [Source GeoIP: Unknown]
    [Destination GeoIP: Unknown]
Internet Control Message Protocol
    Type: 8 (Echo (ping) request)
    Code: 0
    Checksum: 0x62fb [correct]
    Identifier (BE): 0 (0x0000)
    Identifier (LE): 0 (0x0000)
    Sequence number (BE): 0 (0x0000)
    Sequence number (LE): 0 (0x0000)
    [No response seen]
        [Expert Info (Warn/Sequence): No response seen to ICMP request in frame 13]
            [No response seen to ICMP request in frame 13]
            [Severity level: Warn]
            [Group: Sequence]
    Data (22 bytes)
        Data: 740065006f0074006900680075006100630061006e00
        [Length: 22]

0000  0a 02 02 02 02 02 0a 01 01 01 01 01 08 00 45 00   ..............E.
0010  00 32 00 01 00 00 40 01 66 94 0a 00 00 0d 0a 00   .2....@.f.......
0020  00 2a 08 00 62 fb 00 00 00 00 74 00 65 00 6f 00   .*..b.....t.e.o.
0030  74 00 69 00 68 00 75 00 61 00 63 00 61 00 6e 00   t.i.h.u.a.c.a.n.
```

* Jika ingin melihat paket untuk setiap _frame_ , gunakan opsi _-R 'frame.number=NOMOR_FRAME'__ . Misalnya untuk melihat frame nomor 1, gunakan perintah seperti ini:

```
% tshark -V2xr net-0x00.pcap -R 'frame.number==1'
```

* Selanjutnya, perhatikan data dari tiap frame. Bagian yang menarik adalah data (payload) berupa ASCII string dalam format heksadesimal yang terdapat pada paket ICMP (Ping), yaitu:

```
7a37afbc1c270300e5441b49002000000000000000630000000000003abdbd81
ae23d04712d4fb5b2adc576d697185cac5177bcdc974695c5f272092eee2778f
04010006090100200b0700012402f1060107530ab30735d428f6034c23030103
0501005d010001000c00181c0800010acb46c96100000105131166006c006100
67002e0074007800740000001400010a8000494761c9d119150101062000a480
00810000
...
t.e.o.t.i.h.u.a.c.a.n.
```

* String tersebut kemudian kita gabungkan dan ubah menjadi format _binary_ dengan terlebih dahulu melakukan konversi karena data tersebut menggunakan format _big-endian_. Berikut ini adalah script python yang digunakan untuk melakukan konversi:

```python
#!/bin/env python

import array
import binascii

data = '7a37afbc1c270300e5441b49002000000000000000630000000000003abdbd81' \
       'ae23d04712d4fb5b2adc576d697185cac5177bcdc974695c5f272092eee2778f' \
       '04010006090100200b0700012402f1060107530ab30735d428f6034c23030103' \
       '0501005d010001000c00181c0800010acb46c96100000105131166006c006100' \
       '67002e0074007800740000001400010a8000494761c9d119150101062000a480' \
       '00810000'

with open('data.bin', 'wb+') as f:
    b = array.array('H', binascii.unhexlify(data))
    b.byteswap()
    b.tofile(f)
```

* Simpan kode di atas dengan nama __getdata.py__ lalu jalankan. Hasilnya adalah berkas __data.bin__ . Selanjutnya, periksa format berkas tersebut:

```
% python getdata.py
% file data.bin
data.bin: 7-zip archive data, version 0.3
```

* Bisa terlihat bahwa berkas __data.bin__ adalah arsip dengan format 7zip. Selanjutnya, kita bisa memeriksa isi dari arsip tersebut dengan perintah seperti ini:

```

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.utf8,Utf16=on,HugeFiles=on,4 CPUs)

Listing archive: data.bin

--
Path = data.bin
Type = 7z
Method = LZMA 7zAES
Solid = -
Blocks = 1
Physical Size = 163
Headers Size = 131

   Date      Time    Attr         Size   Compressed  Name
------------------- ----- ------------ ------------  ------------------------
2015-11-07 20:39:55 ....A           24           32  flag.txt
------------------- ----- ------------ ------------  ------------------------
                                    24           32  1 files, 0 folders
```

* Bisa terlihat bahwa arsip tersebut diproteksi menggunakan kata kunci (password). Jika memperhatikan _payload_ yang ada pada paket, bisa terlihat _string_ __teotihuacan__. Gunakan string tersebut sebagai kata kunci:

```
% 7z x -pteotihuacan data.bin

7-Zip [64] 9.20  Copyright (c) 1999-2010 Igor Pavlov  2010-11-18
p7zip Version 9.20 (locale=en_US.utf8,Utf16=on,HugeFiles=on,4 CPUs)

Processing archive: data.bin

Extracting  flag.txt

Everything is Ok

Size:       24
Compressed: 164
```

* Berkas __flag.txt__ berhasil diekstrak. Langkah terakhir adalah, melihat isi dari berkas tersebut:

```
% cat flag.txt
flag{MalaguenaSalerosa}
```

* Sekian tutorial kali ini, semoga bermanfaat. Terima kasih kepada Tuhan Yang Maha Esa, Maxindo, N3 dan Anda yang telah meluangkan waktu membaca tutorial ini.
