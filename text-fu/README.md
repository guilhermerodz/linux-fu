# Text-Fu

## stdout

This topic brings us to our next subject: `I/O (input/output) streams`.

- `stdout` means _Standard Out_.

### Example

Let's run the following command:

```sh
$ echo Hello World > potato.txt
```

Check the directory where you ran that command. You should see a file called `potato.txt`, look inside that file and you should see the text "Hello World".
Lots of things just happened in one command so let's breaj it down.

Let's break down the first part:

```sh
$ echo Hello World
```

We know this prints out `Hello World` to the screen, but how? Processes uses I/O streams to receive `input` and return `output`. By default the `echo` command takes the _input_ (standard input or `stdin`) from the keyboard and returns the output (standard output or `stdout`) to the screen. However, **I/O redirection allows us to change this default behavior** giving us greater file flexbility.

Let's proceed to the next part of the command:

The `>` is a redirection operator that allows us to **change where standard output goes**. It allows us to send the output to a file instead of the screen. If the file does not already exists it will create it for us. However, if it does exist it will overwrite it (you can add a shell flag to prevent this depending on what shell you are using).

You can also append the standard output to a existing file instead of overwriting it:

```sh
$ echo Hello World >> potato.txt

$ cat potato.txt
Hello World
Hello World
```
