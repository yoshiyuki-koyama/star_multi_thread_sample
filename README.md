# message_loop_thread_sample
メッセージループ（イベントループ）で動作するマルチスレッド実装サンプル(Rust)

## 概要
```
子スレッド1⇔親スレッド⇔子スレッド2
```
上記のように、それぞれ別の機能を持った複数の子スレッドが親スレッドとメッセージをやり取りしながら動作するマルチスレッドのサンプルです（この実装は親スレッドと一つの子スレッドのみ）。

各スレッドがメッセージループを持ち、イベントドリブンで動くような設計です。
メッセージの送受信には`std::sync::mpsc::channel`の`Sender`、`Receiver`を使っています。

ジェネリクスを利用して、子スレッドの構造体を、親スレッドのデータ型などに依存しないようにしてみました。

## ソースコードのファイル構成
* 親スレッド : `/sample_bin/src/main.rs`
* 子スレッド : `/child_lib/src/lib.rs`
