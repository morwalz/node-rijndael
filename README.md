node-rijndael
=============

A native binding to mcrypt's rijndael encryption with a block size of 256 bits. This allows for the encryption and decryption of data generated by Drupal, which uses rijndael-256, despite the AES standard of rijndael-128.

This module enables interfacing between PHP and Node.js, especially where third-party frameworks like Drupal are involved. Drupal uses rijndael-256 by default, and OPENSSL has no support for any block-side of rijndael apart from 128.

Installation
============

You _will_ need a development version of libmcrypt installed on your system to build node-rijndael.

```sh
# for debian derivatives
$ [sudo] apt-get install libmcrypt-dev
# for red hat derivatives
$ [sudo] yum install libmcrypt-devel
# for arch
$ [sudo] pacman -S libmcrypt
```

<small>If you know how to package an external library with a Node Addon, consider submitting a [pull request][pr].</small>

[npm][]
-------

```sh
$ npm install node-rijndael
```

[github][]
----------

```sh
$ git clone https://github.com/skeggse/node-rijndael.git
```

API
===

As of `0.1.0`, `node-rijndael` will coerce strings into buffers. As of `0.2.0`, `node-rijndael` pads keys and allows key lengths of 16, 24 and 32 bytes.

new Rijndael(key, [options])
-----------------------------

The constructor creates a Rijndael object bound to a specific key, with methods for encrypting and decrypting.

The provided key can be either a `Buffer` or a `string`, and if a string is provided, the `encoding` option will be passed to the `Buffer` constructor.

### Options

```
{
  "encoding": "binary" // default, specifies the key encoding, if applicable
  "mode": Rijndael.MCRYPT_MODE_ECB, // default, the block cipher mode
  "iv": null // default, the initialization vector (uses encoding if a string)
}
```

Rijndael#encrypt(plaintext, [input_encoding, [output_encoding]])
---------------------------

Encrypt the provided `plaintext` with the bound key, and return the encrypted `ciphertext`. `encrypt` will return a `Buffer` by default.

May throw an error if unsupported options provided. Most of the checking should happen in the constructor.

Rijndael#decrypt(ciphertext, [input_encoding, [output_encoding]])
---------------------------

Decrypt the provided `ciphertext` with the bound key, and return the decrypted `plaintext`. `decrypt` will return a `Buffer` by default.

May throw an error if unsupported options provided. Most of the checking should happen in the constructor.

TODO
====

A bit more functionality now, needs tests.

Unlicense / Public Domain
=========================

> This is free and unencumbered software released into the public domain.

> Anyone is free to copy, modify, publish, use, compile, sell, or distribute this software, either in source code form or as a compiled binary, for any purpose, commercial or non-commercial, and by any means.

> In jurisdictions that recognize copyright laws, the author or authors of this software dedicate any and all copyright interest in the software to the public domain. We make this dedication for the benefit of the public at large and to the detriment of our heirs and successors. We intend this dedication to be an overt act of relinquishment in perpetuity of all present and future rights to this software under copyright law.

> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

> For more information, please refer to <[http://unlicense.org/](http://unlicense.org/)>

[pr]: https://github.com/skeggse/node-rijndael/pulls
[encrypt]: https://github.com/skeggse/node-rijndael#rijndaelencryptplaintext-key
[decrypt]: https://github.com/skeggse/node-rijndael#rijndaeldecryptciphertext-key
[npm]: http://npmjs.org/package/node-rijndael "node-rijndael on npm"
[github]: https://github.com/skeggse/node-rijndael "node-rijndael on github"
