
## Patching the client

To actually use the client with the server, you will need to patch it, and I would recommend using [dnSpy](https://github.com/dnSpy/dnSpy) for that.

Also, most of the clients are obfuscated. Please look at the section below on how to patch them.

As far as I know, [b2013606.1](https://osekai.net/snapshots/?version=179) is the latest non-obfuscated version that will work with this server.
There is support for clients from b282 up to the latest osu! stable version.

You will need to find a line inside `osu.Online.BanchoClient` that looks something like this:

![unpatched](https://raw.githubusercontent.com/osuTitanic/clients/main/.github/unpatched.png)

and edit the ip address to match your setup:

![edit](https://raw.githubusercontent.com/osuTitanic/clients/main/.github/edit.png)

![patched](https://raw.githubusercontent.com/osuTitanic/clients/main/.github/patched.png)

And lastly you need to patch every url in dnSpy, from `ppy.sh` to match your domain:

![search](https://raw.githubusercontent.com/osuTitanic/clients/main/.github/search.png)

However, this can be a bit annoying.

You can alternatively use a server switcher, like [ultimate-osu-server-switcher](https://github.com/minisbett/ultimate-osu-server-switcher) to do that.

## Obfuscated clients

Clients are obfuscated most of the time, which means that function names, class names, etc. are not readable anymore:

![obfuscated](https://raw.githubusercontent.com/osuTitanic/clients/main/.github/obfuscated.png)

If you attempt to edit the methods anyways, the decompiler will probably give you some errors.

You can fix these issues using the [de4dot](https://github.com/de4dot/de4dot) deobfuscator. You can download one of the pre-built binaries [here](https://github.com/vee2xx/de4dot-built-binaries). Example:

```shell
de4dot "osu!.exe"
```

The program will output a `osu!-cleaned.exe` file, which you can edit again.
Keep in mind that the function & class names are still not readable.
