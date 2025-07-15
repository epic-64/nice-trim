# nice-trim

Embed multi-line strings in Rust without worrying about indentation.

[![Crates.io](https://img.shields.io/crates/v/nice-trim.svg)](https://crates.io/crates/nice-trim)
[![Documentation](https://docs.rs/nice-trim/badge.svg)](https://docs.rs/nice-trim)
[![License](https://img.shields.io/crates/l/nice-trim.svg)](https://opensource.org/license/mit/)

## 📦 Usage

Add to your `Cargo.toml`:

```toml
nice-trim = "0.1.0"
```

import the `NiceTrim` trait:
```rust
use nice_trim::NiceTrim;
```

Then call the `nice()` method on a `&str`.

```rust
use nice_trim::NiceTrim;

fn main() {
    let text = "
        ███╗   ██╗██╗ ██████╗███████╗ ████████╗██████╗ ██╗███╗   ███╗
        ████╗  ██║██║██╔════╝██╔════╝ ╚══██╔══╝██╔══██╗██║████╗ ████║
        ██╔██╗ ██║██║██║     █████╗█████╗██║   ██████╔╝██║██╔████╔██║
        ██║╚██╗██║██║██║     ██╔══╝╚════╝██║   ██╔══██╗██║██║╚██╔╝██║
        ██║ ╚████║██║╚██████╗███████╗    ██║   ██║  ██║██║██║ ╚═╝ ██║
        ╚═╝  ╚═══╝╚═╝ ╚═════╝╚══════╝    ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝     ╚═╝
    ".nice();
    
    println!("{}", text);
}
```

Output:
```
███╗   ██╗██╗ ██████╗███████╗ ████████╗██████╗ ██╗███╗   ███╗
████╗  ██║██║██╔════╝██╔════╝ ╚══██╔══╝██╔══██╗██║████╗ ████║
██╔██╗ ██║██║██║     █████╗█████╗██║   ██████╔╝██║██╔████╔██║
██║╚██╗██║██║██║     ██╔══╝╚════╝██║   ██╔══██╗██║██║╚██╔╝██║
██║ ╚████║██║╚██████╗███████╗    ██║   ██║  ██║██║██║ ╚═╝ ██║
╚═╝  ╚═══╝╚═╝ ╚═════╝╚══════╝    ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝     ╚═╝
```

**Warning:**
- The `nice()` method returns a `String`, not a `&str`
- The `nice()` method modifies the string at runtime, so it may not be suitable for performance-critical applications.

## 🔍 Alternatives

### Indoc
For a compiler macro, check out https://github.com/dtolnay/indoc

I highly recommend checking it out, because it modifies the strings at compile time rather than runtime.

### Line Continuation (inbuilt)
```rust
let text = "███╗   ██╗██╗ ██████╗███████╗ ████████╗██████╗ ██╗███╗   ███╗\n\
            ████╗  ██║██║██╔════╝██╔════╝ ╚══██╔══╝██╔══██╗██║████╗ ████║\n\
            ██╔██╗ ██║██║██║     █████╗█████╗██║   ██████╔╝██║██╔████╔██║\n\
            ██║╚██╗██║██║██║     ██╔══╝╚════╝██║   ██╔══██╗██║██║╚██╔╝██║\n\
            ██║ ╚████║██║╚██████╗███████╗    ██║   ██║  ██║██║██║ ╚═╝ ██║\n\
            ╚═╝  ╚═══╝╚═╝ ╚═════╝╚══════╝    ╚═╝   ╚═╝  ╚═╝╚═╝╚═╝     ╚═╝";
```