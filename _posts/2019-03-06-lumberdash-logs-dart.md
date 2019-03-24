---
layout: post
title: "Announcing lumberdash: capture logs in Dart and extend its API with custom plugins"
description: "Capture logs in Dart and extend its API with custom plugins"
tags: [dart, flutter, logs, simple api, plugins, sentry]
---

![lumberdash icon](https://raw.githubusercontent.com/jorgecoca/lumberdash/master/art/lumberdash.png)

Do you need logs? [Lumberdash](https://github.com/jorgecoca/lumberdash) is the answer! With a simple but powerful API, Lumberdash is the easiest way to record logs. 
And if that is not enough, you can extend its API and create your own custom plugins for your own logging needs.

## How it works

Simply `putLumberdashToWork` with your preferred `LumberdashClient`, and start logging!

```dart
import 'package:lumberdash/lumberdash.dart';

void main() {
  putLumberdashToWork(withClient: SimpleClient());
  logWarning('Hello Warning');
  logFatal('Hello Fatal!');
  logMessage('Hello Message!');
  logError(Exception('Hello Error'));
}
```

However, you can get the best of **Lumberdash** by using plugins! For example, by using the `colorize_lumberdash`, you could print logs in stdout with colors:

```dart
import 'package:lumberdash/lumberdash.dart';
import 'package:colorize_lumberdash/colorize_lumberdash_client.dart';

void main() {
  putLumberdashToWork(withClient: ColorizeLumberdash());
  logWarning('Hello Warning');
  logFatal('Hello Fatal!');
  logMessage('Hello Message!');
  logError(Exception('Hello Error'));
}
```

You can get this output:

![colorized](https://raw.githubusercontent.com/jorgecoca/lumberdash/master/art/colorized.png)

## Existing plugins

- [colorize_lumberdash](https://pub.dartlang.org/packages/colorize_lumberdash)
- [sentry_lumberdash](https://pub.dartlang.org/packages/sentry_lumberdash)

### How to create a Lumberdash plugin

Add `lumberdash` to your dependencies, and extend the `LumberdashClient`. That easy!

You can see the `SimpleClient` in this package as inspiration.
