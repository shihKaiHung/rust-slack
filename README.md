# rust-slack

A rust crate for sending messages to Slack via webhooks.

[Slack](https://slack.com/) is a messaging platform for team collaboration.

[![Build Status](https://travis-ci.org/frostly/rust-slack.png?branch=master)](https://travis-ci.org/frostly/rust-slack)

# Usage

Add the crate to your existing project:

```rust
extern crate slack;
use slack::{Slack, Payload, PayloadTemplate};

fn main() {
    let slack = Slack::new("https://hooks.slack.com/services/abc/123/45z");
    let p = Payload::new(PayloadTemplate::Complete {
      text: "test message",
      channel: Some("#testing"),
      username: Some("My Bot"),
      icon_url: None,
      icon_emoji: Some(":chart_with_upwards_trend:"),
      attachments: None,
      unfurl_links: Some(true),
      link_names: Some(false)
    });

    let res = slack.send(&p);
    match res {
        Ok(()) => println!("ok"),
        Err(x) => println!("ERR: {}",x)
    }
}
```

# Documentation

[rust-slack documentation](http://open.frostly.com/rust-slack)

# License

This library is distributed under similar terms to Rust: dual licensed under the MIT license and the Apache license (version 2.0).

See [LICENSE-APACHE](LICENSE-APACHE), [LICENSE-MIT](LICENSE-MIT), and [COPYRIGHT](COPYRIGHT) for details.
