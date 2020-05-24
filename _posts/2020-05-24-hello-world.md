---
title: Hello World
tags: Code
author: Edison
mathjax: true
---

Please ignore. 
{:.error}

Testing the following:
* Bullet One
* Testing features. 这是汉字
* Testing `in-line` markdown.

Counting to three:
1. One
2. Two
3. Three


# Code

## Example in Go

```go
package main

import (
	"log"
	"math/rand"
	"sync"
	"time"
)

func worker(part string) {
	log.Println(part, "worker begins part")
	time.Sleep(time.Duration(rand.Int63n(1e6)))
	log.Println(part, "worker completes part")
	wg.Done()
}

var (
	partList    = []string{"A", "B", "C", "D"}
	nAssemblies = 3
	wg          sync.WaitGroup
)

func main() {
	rand.Seed(time.Now().UnixNano())
	for c := 1; c <= nAssemblies; c++ {
		log.Println("begin assembly cycle", c)
		wg.Add(len(partList))
		for _, part := range partList {
			go worker(part)
		}
		wg.Wait()
		log.Println("assemble.  cycle", c, "complete")
	}
}
```

## Example in Rust

```rust
use std::sync::{Arc, Mutex};
use std::thread;

fn main() {
    let counter = Arc::new(Mutex::new(0));
    let mut handles = vec![];

    for _ in 0..10 {
        let counter = Arc::clone(&counter);
        let handle = thread::spawn(move || {
            let mut num = counter.lock().unwrap();

            *num += 1;
        });
        handles.push(handle);
    }

    for handle in handles {
        handle.join().unwrap();
    }

    println!("Result: {}", *counter.lock().unwrap());
}
```

# Math

When $$a \ne 0$$, there are two solutions to $$ax^2 + bx + c = 0$$ and they are

$$x_1 = {-b + \sqrt{b^2-4ac} \over 2a}$$

$$x_2 = {-b - \sqrt{b^2-4ac} \over 2a} \notag$$

# Additional Styles

This is a success message in green
{:.success}

And an error tag
`error`{:.error}

[Documentation](https://tianqi.name/jekyll-TeXt-theme/docs/en/additional-styles)

