<img src="assets/logo.png" width="112" height="112" alt="Blyx penguin moving a setting slider between two marked limits.">

# ValueBounds

Check a numeric setting against inclusive bounds and explain the violation. This Blyx library is part of the validation and configuration collection.

Treating zero as an absent setting silently restores older values. Carry a presence flag and the identity of the winning layer. [Python, configuration defaults and overrides](https://docs.python.org/3/library/configparser.html)

## Install and run

Install [Blyx 0.2.1](https://www.blyx-lang.space/download) with a Rust toolchain and host linker for native builds.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-valuebounds.git
cd blyx-valuebounds
blyxc native-run example.blyx
blyxc native-run tests.blyx
```

[Run the editable browser example](https://www.blyx-lang.space/play?example=package-valuebounds) · [Package page](https://www.blyx-lang.space/packages/valuebounds) · [Handbook](https://doc.blyx-lang.space/guide/fantail)

## Import the module

Run this in the directory containing your application's entry file.

```sh
git clone --depth 1 --branch v0.1.0 https://github.com/Rahulchaube1/blyx-valuebounds.git vendor/valuebounds
```

```blyx
use vendor::valuebounds::valuebounds;

fn main() {
    let value = 12.0;
    let minimum = 0.0;
    let maximum = 10.0;
    let result = valuebounds_check(value, minimum, maximum);
    if len(result) == 0 { println!("invalid"); return; }
    let mut i = 0;
    while i < len(result) {
        println!(at(result, i));
        i += 1;
    }
}
```

Expected output

```text
0
10
2
```

## API

`valuebounds_check(value, minimum, maximum)`

Returns [in bounds, nearest legal value, absolute distance outside]. Reversed bounds are invalid. Invalid arguments and nonfinite results return an empty vector. Integers carried in numeric vectors use the exact range from −(2^53−1) to 2^53−1.

| Argument | Domain |
| --- | --- |
| value | A finite number |
| minimum | A finite number |
| maximum | A finite number |

## In use

[Fantail](https://github.com/Rahulchaube1/blyx-fantail) uses this module to resolve a layered setting and report where an invalid override came from.

## Verification and contributions

The regression suite in [tests.blyx](tests.blyx) checks the example, boundary cases and invalid inputs. Include a short reproducer and your compiler version in [an issue](https://github.com/Rahulchaube1/blyx-valuebounds/issues). The source is dual-licensed under [MIT](LICENSE-MIT) or [Apache-2.0](LICENSE-APACHE). Read the [artwork notice](assets/NOTICE.txt) for credits.

## Connect with Rahul Chaube

[Portfolio](https://www.rahulchaube1.com/) · [GitHub](https://github.com/Rahulchaube1) · [LinkedIn](https://www.linkedin.com/in/rahulchaube1) · [Hugging Face](https://huggingface.co/oncody) · [X](https://x.com/RahulChaube_) · [EverestQ](https://www.everestqai.com/) · [Contact](https://www.rahulchaube1.com/contact)

[Blyx website](https://www.blyx-lang.space/) · [BlyxTorch](https://www.blyx-lang.space/packages/blyxtorch) · [Handbook](https://doc.blyx-lang.space/) · [Community](https://www.blyx-lang.space/community)

Support Rahul’s open-source work through [GitHub Sponsors](https://github.com/sponsors/Rahulchaube1) or [Buy Me a Coffee](https://buymeacoffee.com/rahulchaube).
