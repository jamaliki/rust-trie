# rust-trie
Python Package With A Trie Implementation in Rust

## Installation

Simply run 
```
pip install -e git+https://github.com/jamaliki/rust-trie.git#egg=rust-trie&subdirectory=rust_trie
```

## Use case

This is mainly meant to help with tokenization. A simple use case would be the following Python code, from [https://github.com/OpenBioML/protein-lm-scaling/blob/main/protein_lm/tokenizer/tokenizer.py](protein-lm-scaling) project:

```
from rust_trie import Trie
from typing import List, Optional


class Tokenizer:
    def __init__(self, tokens: List[str], unk_token_id: Optional[int] = None):
        self.tokens = tokens
        self.trie = Trie(unk_token_id)
        for token in tokens:
            self.trie.add(token)
        if unk_token_id is None:
            self.ids_to_tokens += ["<unk>"]
    
    def __call__(self, sequence: str) -> List[int]:
        return self.trie.tokenize(sequence)

```