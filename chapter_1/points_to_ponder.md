# Base 64 encoding
## Purpose of base 64
One hexadecimal digit is of one nibble (4 bits). Two nibbles make 8 bits which are also called 1 byte.

MD5 generates a 128-bit output which is represented using a sequence of 32 hexadecimal digits, which in turn are 32*4=128 bits. 128 bits make 16 bytes (since 1 byte is 8 bits).

Each Base64 character encodes 6 bits (except the last non-pad character which can encode 2, 4 or 6 bits; and final pad characters, if any). Therefore, per Base64 encoding, a 128-bit hash requires at least ⌈128/6⌉ = 22 characters, plus pad if any.

Using base64, we can produce the encoded output of our desired length (6, 8, or 10). If we choose to decide 8 char long output, it occupies only 8 bytes whereas it was occupying 16 bytes for 128-bit hash output.

So, in addition to security, base64 encoding is also used to reduce the space consumed.

## Purpose of base 64 - II
When you have some binary data that you want to ship across a network, you generally don't do it by just streaming the bits and bytes over the wire in a raw format. Why? because some media are made for streaming text. You never know -- some protocols may interpret your binary data as control characters (like a modem), or your binary data could be screwed up because the underlying protocol might think that you've entered a special character combination (like how FTP translates line endings).

So to get around this, people encode the binary data into characters. Base64 is one of these types of encodings.

Why 64?
Because you can generally rely on the same 64 characters being present in many character sets, and you can be reasonably confident that your data's going to end up on the other side of the wire uncorrupted.