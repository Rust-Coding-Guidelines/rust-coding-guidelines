# G.FUD.06 Parameters Should be compatible with multiple types

**[Level] Advice**

**[Description]**

It could enable parameters to be compatible with multiple types, which is benificial for the scalability of code.


**[Bad Case]**

```rust
// Not Good
fn  three_vowels(word: &String) -> bool {
    let mut vowel_count = 0;
    for c in word.chars() {
        match c {
            'a' | 'e' | 'i' | 'o' | 'u' => {
                vowel_count += 1;
                if vowel_count >= 3 {
                    return true
                }
            }
            _ => voweled_count = 0
        }
    }
    false
}

fn main() {
    let sentence_string = "Once upon a time, there was a friendly curious crab named Ferris".to_string();
    for word in sentence_string.split(' ') {
        if three_vowels(word.to_string()) {
            println!("{} has three consecutive vowels!", word);
        }
    }
}
```

**[Good Case]**

```rust
// Good: Three types could be accepted as parameter here: &String / &str / &'static str.
fn three_vowels(word: &str) -> bool {
    let mut vowel_count = 0;
    for c in word.chars() {
        match c {
            'a' | 'e' | 'i' | 'o' | 'u' => {
                vowel_count += 1;
                if vowel_count >= 3 {
                    return true
                }
            }
            _ => vowel_count = 0
        }
    }
    false
}

fn main() {
    let sentence_string = 
        "Once upon a time, there was a friendly curious crab named Ferris".to_string();
    for word in sentence_string.split(' ') {
        if three_vowels(word) {
            println!("{} has three consecutive vowels!", word);
        }
    }
}
```