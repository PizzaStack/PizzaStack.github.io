# [Return to Index](/README.md)
# I/O Streams
The JVM can connect to sources of data that exist outside itself, from files on the hard drive to network port sockets and of course the standard input/output channels of a console.
- Byte Input Streams
    - **BufferedInputStream** Reads a buffer of bytes from an InputStream, and then returns bytes from the buffer, making small reads more efficient.

    - **ByteArrayInputStream** Reads bytes sequentially from an array.

    - **FileInputStream** Reads bytes sequentially from a file.

    - **ObjectInputStream** Reads binary representations of Java objects and primitive values from a byte stream. This class is used for the deserialization of objects.

- Character Input Streams
    - **BufferedReader** Reads a buffer of characters from a Reader, and then returns characters from the buffer, making small reads more efficient.

    - **FileReader** Reads characters sequentially from a file. An InputStreamReader subclass that reads from an automatically-created FileInputStream.

    - **InputStreamReader** Reads characters from a byte input stream. Converts bytes to characters using the encoding of the default locale, or a specified encoding.

- Byte Output Streams
    - **BufferedOutputStream** Buffers byte output for efficiency; writes to an OutputStream only when the buffer fills up.

    - **FileOutputStream** Writes bytes sequentially to a file.

    - **ObjectOutputStream** Writes binary representations of Java objects and primitive values to an OutputStream. Used for the serialization of objects.

- Character Output Streams
    - **BufferedWriter** Buffers output for efficiency; writes characters to a Writer only when the buffer fills up.

    - **FileWriter** Writes characters sequentially to a file. A subclass of OutputStreamWriter that automatically creates a FileOutputStream.

    - **OutputStreamWriter** Writes characters to a byte output stream. Converts characters to bytes using the encoding of the default locale, or a specified encoding.

    - **PrintWriter** Writes textual representations of Java objects and primitive values to a Writer.

