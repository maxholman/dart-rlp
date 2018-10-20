# rlp

An Ethereum RLP library for Dart - https://pub.dartlang.org/packages/rlp

[![Build Status](https://travis-ci.org/maxholman/rlp.svg?branch=master)](https://travis-ci.org/maxholman/rlp)

> The purpose of RLP (Recursive Length Prefix) is to encode arbitrarily nested arrays of binary data, and RLP is the main encoding method used to serialize objects in Ethereum

`rlp` takes a `String`, `int` or `List` and returns an RLP encoded `List<int>`

## Usage

A simple usage example:

```dart
import 'package:rlp/rlp.dart';

main() {
  var encoded = Rlp.encode(["dog", "cat"]);
  print(encoded); // List<int> [200, 131, 100, 111, 103, 131, 99, 97, 116]
}

```

A more complex usage example:

```dart
import 'dart:typed_data';

import 'package:convert/convert.dart';
import 'package:pointycastle/pointycastle.dart';
import 'package:rlp/rlp.dart';

main() {

  const sender = Address('0xba52c75764d6f594735dc735be7f1830cdf58ddf');
  const nonce = 3515;

  var encoded = Rlp.encode([sender, nonce]);

  var out = new Digest('SHA-3/256').process(Uint8List.fromList(encoded));
  var contractAddress = hex.encode(out.sublist(12));

  print('Cryptokitties contract address is 0x$contractAddress'); // 0x06012c8cf97bead5deae237070f9587f8e7a266d

}

```

## Features and bugs

Please file feature requests and bugs at the [issue tracker][tracker].

[tracker]: https://github.com/maxholman/rlp/issues
