File can be read using *BufferedReader*, *Scanner*, *StreamTokenizer*, *DataInputStream*, *SequenceInputStream,* and *FileChannel*.

### BufferedReader

Simplifies reading text from a character input stream. It buffers the character in order to enable efficient reading of text. It is efficiently used to read text from any kind of input source.

It also minimizes IO operations by reading chunks of characters and store them in an internal buffer. While the buffer has data, the reader will read from it instead of directly from the underlying stream.

**Extending Reader**

BuferredReader expects a Reader in its constructor to extend the reader functionaility.

```java
BufferedReader reader = 
  new BufferedReader(new FileReader("src/main/resources/input.txt"));
```

But, if buffering doesn't matter to us we could just use a *FileReader* directly:

```java
FileReader reader = 
  new FileReader("src/main/resources/input.txt");
```

**Using a stream**

BufferedReader to take any kind of input stream as an underlying source. We can do it using *InputStreamReader* and wrapping it in the constructor:

```java
BufferedReader reader = 
  new BufferedReader(new InputStreamReader(System.in));
```

### BufferedReader vs Scanner

* BR is synchronized and thread-safe

* BR can change the size of the buffer, scanner doesn't 

* BR has larger default buffer size

* 

### Reading Files

**BufferedReader**

To read a large file we can use the BufferedReader.

```java
@Test
public void whenReadWithBufferedReader_thenCorrect()
  throws IOException {
     String expected_value = "Hello, world!";
     String file ="src/test/resources/fileTest.txt";

     BufferedReader reader = new BufferedReader(new FileReader(file));
     String currentLine = reader.readLine();
     reader.close();

    assertEquals(expected_value, currentLine);
}
```

### Writing Files

We'll make use of *BufferedWriter*, *PrintWriter*, *FileOutputStream*, *DataOutputStream*, *RandomAccessFile*, *FileChannel*
