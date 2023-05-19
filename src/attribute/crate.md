<!--
# Crates
-->
# クレート

<!--
The `crate_type` attribute can be used to tell the compiler whether a crate is
a binary or a library (and even which type of library), and the `crate_name`
attribute can be used to set the name of the crate.
-->
`crate_type`アトリビュートは、そのクレートがライブラリ、バイナリのいずれにコンパイルされるべきかをコンパイラに伝えるために使用します。ライブラリの場合は、どのタイプのライブラリであるかも伝えることができます。`crate_name`はクレートの名前を決定するのに使用します。

<!--
However, it is important to note that both the `crate_type` and `crate_name`
attributes have **no** effect whatsoever when using Cargo, the Rust package
manager. Since Cargo is used for the majority of Rust projects, this means
real-world uses of `crate_type` and `crate_name` are relatively limited.
-->
しかし、`crate_type`アトリビュートも`crate_name`アトリビュートも、RustのパッケージマネージャCargoを利用している場合は**何の**影響もないと知っておくことは重要です。Cargoは大半のRustプロジェクトで利用されており、実世界での`crate_type`と`crate_name`の利用は比較的限られています。

```rust,editable
// This crate is a library
// このクレートはライブラリである。
#![crate_type = "lib"]
// The library is named "rary"
// このライブラリの名前は「rary」である。
#![crate_name = "rary"]

pub fn public_function() {
    println!("called rary's `public_function()`");
}

fn private_function() {
    println!("called rary's `private_function()`");
}

pub fn indirect_access() {
    print!("called rary's `indirect_access()`, that\n> ");

    private_function();
}
```

<!--
When the `crate_type` attribute is used, we no longer need to pass the
`--crate-type` flag to `rustc`.
-->
`crate_type`アトリビュートが使用されているときは、`rustc`に`--crate-type`フラグを伝える必要はありません。

```shell
$ rustc lib.rs
$ ls lib*
library.rlib
```
