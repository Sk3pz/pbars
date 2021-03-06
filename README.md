# pbars
A rust crate for progress bars in the terminal.  
![image](example_images/ss.png)
### Example:
```rust
use pbars::{PBar, BarType};
use std::thread::sleep;
use std::time::Duration;

fn main() {
    // using crossterm, this will create a pbar at 0,0
    // without crossterm, this is the only way to create a bar
    let mut pbar = PBar::new(BarType::Bar, true, true, 20);

    for x in 0..1000 {
        // get the percentage complete as a decimal
        let percentage_decimal = x as f32 / 1000.0;
        // scale the percentage from 0..1 to 0..100 and convert to a u8
        let percent = (percentage_decimal * 100.0) as u8;
        // update the pbar
        pbar.update(percent);
        // draw the pbar
        pbar.draw();
        // delay for 10ms, making this run in 10 seconds
        sleep(Duration::from_millis(10));
    }
}
```
