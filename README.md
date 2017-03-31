[Development log](https://fish.dontexpectanythingsensible.uk) for our fishing game.

![](img/first-screenshot.png)

## Development

Static site generated with [cobalt](https://github.com/cobalt-org/cobalt.rs):
* Install Rust and Cargo
* `cargo install cobalt`
* `cobalt build` or `cobalt watch -P 3003` // runs on localhost:3003

All posts in `/posts` as Liquid templates; all other files/folders are copied as-is into `/build`.


### Todo
- sass
- cachebusting css
- favicon
